# Machine-description format (draft v0.1)

The highest-leverage single piece of the software (see `software.md`): every plug-in, every handoff, and the internal coordinate system all depend on how a build's hardware is described. Get this wrong and it has to change under everything built on top of it — so it's worth pinning down before anything else.

## Design goals

- **Adapts to whatever someone actually built.** `hardware.md` is explicit that rail height, arm reach, tool count, and dock count all vary build to build. The format has to describe an arbitrary build, not assume everyone converges on one reference geometry.
- **Minimal, like the standard itself.** The top-level README keeps the standard to motion coverage, a tool-docking interface, and interoperability — on purpose, so it doesn't lock the ecosystem into today's best guess at a connector. This format follows the same rule: it declares *that* a dock uses a given docking interface, it doesn't try to standardize the interface itself.
- **Open-ended tool set.** `tool-family.md` treats additive/subtractive/electronics tools as examples, not a fixed catalog. The format can't hardcode a fixed parameter schema per tool type without a version bump every time someone adds a new kind of tool.
- **Human-authored first.** Plain YAML, readable and hand-editable — the same reason Klipper's `printer.cfg` is plain text, not a binary blob. A GUI/wizard that generates this file is a reasonable v2, not required for v1.

## Draft schema

```yaml
schema_version: 0.1

machine:
  name: my-build
  kinematics: core-xy       # stock Voron 2.4 assumption, but declared, not hardcoded
  build_volume: {x: 350, y: 350, z: 700}   # mm, full working envelope
  origin: front-left-bottom # anchors the coordinate system every plug-in's output gets translated into

rails:
  - id: z-rail-1
    axis: z
    travel: 700              # mm

arm:
  mounted_on: [z-rail-1]      # shares the rail per the "no separate frame" design goal
  reach: 150                  # mm, working extension from the mount point
  dof: 1                       # rotary/extra axes beyond the shared gantry rails

docks:
  - id: dock-1
    position: {x: 0, y: 0, z: 650}
    interface: toolchanger-v1   # names the physical/electrical docking standard in use; not standardized by this project
    accepts: [fdm-hotend, laser-head]

tools:
  - id: fdm-hotend
    type: additive
    docks_at: [dock-1]
    params: {nozzle_diameter: 0.4, max_temp: 280}
  - id: laser-head
    type: subtractive
    docks_at: [dock-1]
    params: {wavelength_nm: 450, max_power_w: 40}
```

## Why these sections

- **`origin`** exists because `software.md` needs "a consistent internal coordinate system that every plug-in's output gets translated into" — this field is the anchor that translation is relative to.
- **`arm` is separate from `rails`** because it rides on the shared rails but has its own reach and degrees of freedom, and both vary independently build to build.
- **`docks[].interface` is a name, not a spec.** This format says which docking standard a build uses; it deliberately doesn't define connector pinouts or mechanical tolerances, matching the standard's own minimalism.
- **`tools[].params` is an open bag**, not a fixed set of fields, so a new tool type doesn't require bumping `schema_version` just to add a parameter no existing tool needed.

## Open questions

- How much of `params` is standardized versus plug-in-specific — does `nozzle_diameter` mean the same thing to every FDM plug-in, or does each plug-in define its own expected param names, with this format just passing them through?
- Whether `docks_at` needs orientation, not just position, once an arm's `dof` is greater than 1.
- How the pause/handoff authoring format (still open in `software.md`) references this file — a handoff needs to know which dock the outgoing tool releases and which tool docks in next, so it likely reads `docks[]` and `tools[]` directly.
- Whether YAML stays the source format long-term, or becomes a generated artifact once there's tooling that authors it for people who don't want to hand-write config.
