# Blender Modeling Skill

A reusable Codex skill for building editable Blender models from photographs, drawings, or descriptions, then improving them through rendered comparisons.

## What it covers

- Reference analysis, proportions, dimensions, and camera matching.
- Python-based modeling with editable geometry and modifiers.
- Props, vehicles, toy cars, and manufactured assemblies.
- Human heads, likeness studies, optional MPFB bases, and hair.
- Checkpoints, multi-view review, targeted revisions, and practical stopping criteria.
- Blender connection and command-line execution guidance.

The skill defaults to built-in Blender tools and free assets/add-ons. It is an instruction package, not a Blender add-on, executable model generator, or photogrammetry engine. It does not install Blender or MPFB automatically.

## Files

```text
blender-modeling/
  SKILL.md
  agents/openai.yaml
  references/blender-execution.md
  references/hard-surfaces.md
  references/people-and-faces.md
```

## Use

Install the complete `blender-modeling` folder in a skill location supported by your Codex installation, or ask Codex's skill installer to install the `blender-modeling` directory from this repository. Keep its reference files together with `SKILL.md`.

Attach your pictures and ask:

> Use $blender-modeling to build this toy car from the attached photos. Keep it editable, match the 12 cm overall length, and refine it through front, side, and three-quarter renders.

Or, for an existing project:

> Use $blender-modeling to improve this Blender model against these reference pictures. Preserve my manual edits and compare the changes with the original.

Specify whether the result is for a still render, animation, a game, or 3D printing. Include multiple views and one known dimension when available. Hidden geometry inferred from one photograph cannot be guaranteed to match the real object.

## Requirements and validation

Use a Codex environment that can access a Blender installation and inspect generated images. A working Blender connector is useful; background Blender scripting is an alternative. MPFB is optional and only relevant to human bases.

The skill structure and local reference links were validated. Its guidance includes lessons from an actual MPFB/Python face study, including duplicate shape-key prevention and multi-view hair review. The packaged skill has not yet been tested end to end on a new object; it does not guarantee photorealism or production-ready geometry.

This repository contains workflow instructions only. Blender projects, reference photographs, textures, and third-party add-on code are not bundled. Referenced software and assets retain their respective licenses.
