# firmware

Onboard control code, split by what it runs on.

- `gantry/` — core-XY motion control (the base Voron 2.4's existing motion system)
- `arm/` — motion control for the arm mounted above, sharing the base machine's vertical rails
- `tool-coupling/` — firmware for whatever tool-changing approach this build uses

No logic yet — structure only. See `/docs/hardware.md` and `/docs/software.md`.
