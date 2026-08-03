# Tool family

Tool changing is a solved problem (Stealthchanger and others) — use whatever suits your build. This doc is about what tools the software (see `software.md`) needs to know how to route work to, not a hardware spec.

## No process here is novel

FDM, continuous fiber, polyjet, CNC milling, laser cutting, and PCB/conductive trace printing are all established techniques individually. Combining them on one machine isn't new mechanically — the point of this project is software that can route work to whichever of them a given builder has, on whatever hardware they've put together.

## Additive (examples)

| Tool | Role |
|---|---|
| FDM | Bulk volume buildup |
| Continuous fiber | Strength / conductivity |
| Polyjet | Texturing / finishing |

## Subtractive (examples)

| Tool | Role |
|---|---|
| Small CNC spindle/router | Precision finishing, pocketing, drilling — cleanup that additive alone can't hold tolerance on |
| Laser (cutting/engraving) | Cutting, engraving, marking, and potentially selective curing/sintering depending on power |

## Electronics (examples)

| Tool | Role |
|---|---|
| PCB / conductive trace print head | Printed circuit traces directly on or embedded in the part |
| Embedded component placement | Placing discrete components (pick-and-place style) into a part mid-build |

This is the category that ties structural, decorative, and functional together in one build — a part can come off the machine with its circuitry already embedded, not assembled afterward.

## Why this list matters for the software, not the hardware

The base program (`software.md`) needs to know which tools and toolpath generators a build is combining, since each one's output has to be ingested in its native format. In v1, the designer decides which tool handles which part of the job by placing pause points by hand — this list is what they're choosing between, not a fixed catalog anyone has to build to.
