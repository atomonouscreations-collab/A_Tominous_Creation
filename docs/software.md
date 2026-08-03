# Software — the actual project

This is a software project more than a hardware one. The ecosystem software is the meeting point where different manufacturing technologies come together — planar slicers, non-planar slicers, CAM software, laser tools — pulled in as plug-ins rather than run as separate disconnected programs. It doesn't implement any specific toolpath generation method itself; that's not the value it adds.

## Why plug-ins, not native generation

Every method here — planar slicing, non-planar slicing, CAM, laser toolpath generation — already has existing software solving it, in varying states of maturity. Duplicating any of that inside the ecosystem software would mean maintaining a worse copy of something that already works. The value of this project isn't out-slicing any of those tools individually; it's giving them a shared place to combine, so a designer can move between them on one job instead of juggling separate programs with no way to hand off between them.

## v1: manual, designer-defined handoffs

At first, users and designers are responsible for deciding which method runs when: pause one plug-in's output at a chosen point, hand off to another plug-in, then resume. The mechanism is the same idea as a manual filament-change pause, generalized across whatever plug-ins are wired in.

## What the ecosystem software needs to do (v1)

- Provide a plug-in interface (see the gRPC/Protocol Buffers direction, modeled on CuraEngine's plugin architecture) that existing slicers — planar and non-planar — plus CAM software and laser tools can be wrapped by, invoked from inside the ecosystem software rather than run separately.
- Keep a consistent internal coordinate system that every plug-in's output gets translated into, so handoffs between plug-ins don't introduce positional error.
- Let a designer mark pause/handoff points where control passes from one plug-in to another.
- Handle tool-change/dock logistics at each handoff, where applicable.

## Where this could go later

Automatic segment classification — deciding which plug-in fits which region of a part without a person marking the handoff by hand — is a longer-term goal, not what v1 needs. A healthy plug-in ecosystem is the actual long-term goal: the more methods that exist as plug-ins — including better non-planar slicers as they're developed — the more useful the software gets without the project itself having to build or maintain any of them directly.

## Open questions

- Plug-in interface design: what a plug-in has to implement to be wired into the ecosystem software (how it receives geometry/parameters, what format it has to return toolpaths in).
- The internal coordinate system/representation every plug-in's output gets translated into, and how much translation burden that puts on plug-in authors versus the host.
- How pause/handoff points get authored — inline markers, a separate manifest, a small GUI — and how much of that a designer has to do by hand.
- How different plug-ins stay visually and mechanically consistent at a handoff (layer height, feed rate, etc. matching up) even though they come from completely different code paths and, likely, different authors.
- Which existing non-planar slicers are mature enough to wrap as plug-ins now versus which parts of non-planar coverage still have no good existing option to plug in.
