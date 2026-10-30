---
name: blender-modeling
description: Build and refine editable 3D models in Blender from photographs, drawings, or descriptions using Python and rendered comparisons. Use for reference-based props, vehicles, products, environments, and people or faces, including revisions to existing Blender models. Does not turn a request for a rendered image alone into a 3D modeling project.
---

# Blender Modeling

Produce an editable Blender model whose geometry, silhouette, and materials hold up against the supplied references. Use Python for repeatable construction and adjustments, and actual Blender renders for visual judgment. Default to built-in tools and free assets/add-ons; paid services are optional only when the user chooses them.

## Start with the actual project

- Identify the subject, supplied references, existing `.blend`, and intended use. A still render, animated asset, and printable object require different geometry checks. Infer a reasonable first milestone when the brief is open-ended.
- Inspect available images. Front, side, rear, top, and three-quarter views plus one dimension help constrain a manufactured object. For a face, seek front/profile/three-quarter photographs with reasonably compatible age and expression.
- Separate visible facts from inferred geometry. One photograph cannot establish hidden surfaces or exact dimensions. Proceed with disclosed assumptions when a plausible interpretation is sufficient; ask only for information that materially blocks the requested result.
- Separate manual reconstruction from a capture/reconstruction pipeline. Do not claim photogrammetry or exact recovery from a few unrelated pictures. Investigate a capture pipeline separately when the user supplies a suitable overlapping photo set and requests that approach.

## Choose the modeling approach

Read only the relevant supporting guidance:

- **Props, toy cars, vehicles, products, and assemblies:** [references/hard-surfaces.md](references/hard-surfaces.md).
- **People, anatomical heads, likenesses, MPFB, and hair:** [references/people-and-faces.md](references/people-and-faces.md). MPFB is optional and specific to human bases.
- **Before executing Blender scripts or connecting to a session:** [references/blender-execution.md](references/blender-execution.md).

For other subjects, choose the simplest useful mesh, curve, sculpt, instancing, or Geometry Nodes construction. Do not impose a human workflow on unrelated geometry. Use targeted official documentation or a focused tutorial for an unfamiliar operation; there is no need to study a complete course before starting a familiar task. Distinguish read/watched demonstrations from techniques actually executed and verified.

## Build and compare

1. Preserve the starting file and any unsaved work. Inspect the current scene and create a clearly named project collection or scene. Scope deletion/replacement to generated objects owned by this project; keep manual edits recoverable.
2. Establish units, principal axes, approximate bounds, and reference cameras. Match perspective before changing shape to fit a photograph. Use orthographic review views for structure, but do not treat perspective photos as orthographic blueprints.
3. Build the major silhouette and proportions first. Keep meaningful parts, parameters, and modifiers editable. Add secondary features only when the blockout works from multiple views; materials and fine texture should follow shape.
4. Save a checkpoint and render a small review set appropriate to the subject. Inspect those images with an image-viewing tool. A successful script or saved file does not establish visual quality.
5. Name the most important visible mismatch, change the smallest related parameter group, then rerender comparable views. Retain a change only when the overall result improves; compare against the reference and best checkpoint, not merely the previous attempt.
6. If further iteration is authorized, continue while changes make clear progress. When successive targeted passes mostly trade one defect for another or make negligible visible gains, retain the best version and explain the remaining limitation. There is no fixed pass quota. Do not mistake a failed script, stale render, duplicate deformation, or unchanged parameters for diminishing returns.

For longer loops, keep a compact log: checkpoint, hypothesis, actual change, rendered views, observation, and keep/revert decision. Avoid unsupported numerical likeness scores. Keep camera, lighting, and resolution stable when comparing geometry; document intentional presentation changes.

## Deliver and verify

- Save the chosen `.blend`, scripts/configuration needed to reproduce or adjust it, and representative review renders. Pack redistributable textures or include dependencies explicitly; record external asset licenses.
- Verify the saved file reopens, expected objects and modifiers exist, transforms/dimensions make sense, and material image dependencies resolve. Inspect evaluated geometry when modifiers determine the final shape.
- Check purpose-specific requirements when relevant: deformation for animation, export round trip for a requested export, manifold closed geometry and real scale for printing. Do not label a model production-ready based on appearance alone.
- If the user is working in live Blender, load or show the accepted result without discarding unsaved changes, then verify the actual session state. Distinguish that from a background render.
- Show an actual render, link the editable project, summarize what improved, and state remaining visible limitations. A comparison sheet may arrange original renders without retouching the model's appearance.

Keep project assets, checkpoints, and source images in the project's workspace. This skill contains reusable guidance, not a shared working scene or a requirement to reuse a previous subject's parameters.
