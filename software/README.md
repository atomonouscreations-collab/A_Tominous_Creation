# software

This is the actual project (see `/docs/software.md`). Host-side software — everything that isn't running on the machine itself.

- `slicer-integration/` — the ecosystem host and its plug-in interface — the meeting point where different toolpath technologies get pulled in, not a generator of any of them
- `plugins/` — plug-ins wrapping already-existing methods (planar slicers, non-planar slicers, CAM, laser) into that interface
- `scheduler/` — handles tool-change/dock logistics at each designer-placed handoff point between plug-ins
- `sim/` — simulation/visualization for checking a combined job before running it on real hardware

No logic yet — structure only.
