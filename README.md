# A_Tominous_Creation

More a software project than a hardware one.

## Status

Concept / pre-hardware. Documentation in progress. Not yet built.

## The idea

The hardware is simple, and it's not the point: an extended-height Voron 2.4 with a simple arm mounted above the base machine, sharing the same vertical linear rails rather than needing its own frame. Motion systems and tool changers (Stealthchanger and others) are already solved problems in the Voron/RepRap-derived community — build it however suits you, there's no fixed way it has to be done.

What doesn't exist yet is the software: an ecosystem program that's the meeting point for the different manufacturing technologies — planar slicers, non-planar slicers, CAM, laser — pulled in as plug-ins rather than run as separate disconnected programs. It doesn't implement any specific toolpath generation method itself; several already exist for each, including non-planar slicers, and duplicating that work isn't the point. At first, the designer decides which method runs when, by pausing one plug-in's output at a chosen point and handing off to another, the same way a manual filament-change pause works, just generalized across whatever plug-ins are wired in.

- **`docs/hardware.md`** — the base machine, and why it's kept simple on purpose.
- **`docs/software.md`** — the actual project: what the toolpath generator needs to do and why that's the hard, useful part.
- **`docs/tool-family.md`** — the tools the software needs to route work to.

## Why open source

This design isn't being patented. The goal is to document it publicly, openly, and early enough that it stays available for anyone to build on — makers, other toolchanger projects, small manufacturers — rather than getting locked up by whoever files first.

## License

- Hardware (mechanical designs, schematics, BOMs): [CERN-OHL-S v2](hardware/LICENSE) (strong reciprocal — derivatives must stay open).
- Software / firmware: [GPLv3](LICENSE) — matches Klipper, the likely firmware base, and keeps the same reciprocal spirit as the hardware license.

## Repo structure

```
hardware/       CAD, electrical schematics, BOMs — kept minimal, base is an extended Voron 2.4
firmware/       gantry/, arm/, tool-coupling/ — onboard control code
software/       slicer-integration/, plugins/, scheduler/, sim/ — the actual project: a plug-in host where planar, non-planar, CAM, and laser toolpath technologies come together
docs/           hardware, software, tool family, funding plan, build log
tests/
scripts/
```

Structure only for now — no logic yet. Each folder has its own README describing what will live there.

## Contributing

See `CONTRIBUTING.md`.

## Funding / project status

See `docs/funding-plan.md` for the open-hardware funding roadmap (Hackaday Prize, NLnet, Crowd Supply, build log).
