# Hardware

Kept deliberately simple, because the hardware isn't the point.

## The base machine

An extended-height Voron 2.4 — same vertical linear rails as the stock design, just taller — with a simple arm mounted above the base machine, sharing those same vertical rails rather than needing its own frame.

## Motion and tool changing are solved problems

Core-XY, toolchangers (Stealthchanger and others), linear rail motion — all of this is well-worn, well-documented territory in the Voron and broader RepRap-derived community. Nobody needs a new standard for it. Build it however suits you: use the existing designs, adapt them, mix parts from different projects. The hardware side of this project isn't inventing new mechanics, and it isn't prescribing one correct way to build it.

## What actually varies build to build

Rail height, arm placement and reach, which tools someone has, how many docks they've set up — all of that is going to differ from one person's build to the next, and that's fine. It's expected. That variability is exactly why the real work is on the software side (see `software.md`): the toolpath generator has to adapt to whatever hardware configuration someone actually built, not assume everyone converges on one fixed geometry.
