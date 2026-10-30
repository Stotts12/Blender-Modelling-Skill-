# Executing and validating Blender work

## Inspect the environment first

Discover available Blender tools or connectors and read their actual schemas. Query the running version, open file, active scene, dirty state, and relevant objects before changing an existing project. Prefer a working Blender connector for live session inspection and edits.

If no connector is available, locate the installed Blender executable and use its bundled Python through the command line. The conventional macOS location is `/Applications/Blender.app/Contents/MacOS/Blender`, but verify it rather than assuming. Ordinary system Python does not include Blender's `bpy` module.

Use background Blender for isolated checkpoints and repeatable renders when appropriate. A typical command structure is:

```text
<blender-executable> --background <checkpoint.blend> --python-exit-code 1 --python <script.py> -- <settings.json>
```

Resolve and quote real project paths. Blender argument order matters: load the intended file before running the script; script arguments follow `--`. Save logs and check both process exit status and expected output files. Use bounded waits and inspect logs when an operation stalls.

A background process changes files on disk; the already-open Blender window will not automatically show the new result. Before loading it into the live session, inspect unsaved state and preserve a separate copy if needed. Requery the live scene afterward.

## Connection fallback

The original project used an installed Blender MCP add-on with a local TCP bridge at `127.0.0.1:9876`, accepting JSON of the form `{"type":"execute_code","params":{"code":"..."}}`. This is a project-specific observation, not a universal MCP protocol. Use it only after confirming the installed add-on and endpoint support that request. Prefer exposed tools when available; do not send code to an arbitrary discovered port.

Do not reinstall or restart a functioning Blender session merely because the connector is absent from a new chat. Inspect the actual situation and choose a script fallback if it meets the task. Installation or connection changes should be scoped to what the user requested and what the workflow needs.

## Reliable scripts and checks

- Keep script files and settings alongside the project; use explicit object references instead of relying on whichever object happens to be selected. Prefer data APIs when operators require fragile mode/context setup.
- Make repeated generation update or replace only known generated components. Never begin by deleting every object in the user's scene. Save checkpoints before replacing generated components that may have been manually edited.
- Avoid accumulating targets, modifiers, materials, or object copies on each run. A small re-run check on a disposable checkpoint is useful for generators intended to be repeatable.
- Track source settings and actual output identity so a failed rerender cannot be mistaken for a fresh result. Do not apply a speculative edit to every checkpoint.
- Keep preview renders inexpensive while evaluating shape. Increase samples/resolution after selecting the geometry; high-quality rendering cannot correct proportions.
- Use a few meaningful assertions tied to the intended model: expected generated components, finite geometry, plausible evaluated dimensions, intended target values, or required external dependencies. Do not require arbitrary object/vertex counts as a proxy for quality.
- In face workflows, check shape-key reuse and asset fitting; see [people-and-faces.md](people-and-faces.md). In assemblies, check relationships between parts; see [hard-surfaces.md](hard-surfaces.md).

Inspect actual rendered images after running code. Report whether the deliverable was merely generated, visually reviewed, reopened, or also checked in the live application. Keep those claims distinct.
