# software/slicer-integration

The ecosystem host — the core of the project (see `/docs/software.md`). Exposes a plug-in interface that lets existing toolpath technologies (planar slicers, non-planar slicers, CAM, laser) be pulled in and invoked from inside the ecosystem software. Doesn't generate toolpaths itself — the plug-ins do that; the host is the meeting point between them. Plug-in output gets translated into a shared internal coordinate system so handoffs between plug-ins stay aligned.
