# A_Tominous_Creation — where different manufacturing technologies come together

## The problem

Most 3D printers do one process well. The moment you want bulk volume, structural reinforcement, a finished surface, embedded electronics, or precision subtractive cleanup on the same part, you're looking at a handful of separate machines and separate software for each — or an expensive proprietary system that locks you into one vendor's tools.

## The hardware isn't the interesting part

The base machine here is an extended-height Voron 2.4 with a simple arm mounted above it, sharing the same vertical linear rails. That's it. Motion systems and tool changers — core-XY, Stealthchanger, the rest — are already solved problems in the Voron/RepRap-derived community. No new mechanical invention here, and no fixed way it has to be built.

## The actual project: a meeting point, not a new engine

Planar slicing, non-planar slicing, CAM, laser toolpath generation — all of these already have existing software solving them, in varying states of maturity. This project doesn't try to out-build any of them. It's the ecosystem software that pulls them all in as plug-ins, so a designer can move between technologies on one job instead of juggling separate programs with no way to hand off between them.

At first, the designer is responsible for deciding which method runs when: pause one plug-in's output at a chosen point, hand off to another, then resume. It's the same idea as a manual filament-change pause, generalized across whatever plug-ins are wired in. Automatic routing is a longer-term goal, not what's needed to get something useful working.

Full writeup: `docs/hardware.md` for the base machine, `docs/software.md` for the plug-in architecture, `docs/tool-family.md` for the tools it needs to support.

## Why open source, not patented

This design isn't being filed as a patent. It's being published openly and documented from day one so it stays available to build on — for other toolchanger projects, for makers, for anyone trying to solve the same multi-process problem — rather than getting locked up by whoever files first.

## Status

Concept and design-doc stage. No hardware or software built yet. Open questions on the software side — the plug-in interface, the internal coordinate system every plug-in translates into, which existing non-planar slicers are mature enough to wrap now — are in `docs/software.md`.

Following along, have feedback, or already working on something like this? Open an issue — prior-art references are especially welcome, they keep the documentation honest.
