# Design overview

This is more a software project than a hardware one. Three documents cover it:

- **`hardware.md`** — the base machine: an extended-height Voron 2.4 with a simple arm mounted above it, sharing the same vertical rails. Motion and tool changing are already-solved problems — build it however suits you.
- **`software.md`** — the actual project: an ecosystem program that's the meeting point for different toolpath technologies — planar slicers, non-planar slicers, CAM, laser — pulled in as plug-ins rather than implemented natively. Starts with manual designer-placed pause points rather than automatic routing.
- **`tool-family.md`** — the tools the software needs to route work to: additive, subtractive, and electronics, as examples rather than a fixed catalog.

No single process here is novel, and the hardware isn't either — it's a straightforward extension of well-established open designs. What's actually being built is software flexible enough that someone can put together their own version of the hardware and have working software for it from day one.
