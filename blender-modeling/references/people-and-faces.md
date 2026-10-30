# People, faces, and MPFB

## Establish structure before likeness detail

Choose manual mesh/sculpt construction or a reusable human base according to the request. MPFB can provide a free editable human base; it does not solve likeness automatically. Do not force its installation when a suitable base already exists or the user wants manual construction.

Compare cranium, face length/width, jaw angle, chin projection, cheek volume, eye spacing and sockets, nose bridge/tip, and mouth placement across front, profile, and three-quarter views. Check the spaces and relationships between features. Expression, camera angle, focal length, and age differences in photographs can look like shape errors.

Develop eyelids around the eyeballs, a lip meeting line with surrounding volume, nostril cavities, and ear structure. Introduce intentional asymmetry after the broad structure is coherent. Preserve a symmetric base when later retopology or expressions would benefit from it.

For a still-image study, dense sculpting can be appropriate. Animation requires suitable topology and deformation checks; a detailed sculpt alone does not establish that. A head crop or mask generally leaves an open surface and is not print-ready.

## MPFB scripting lessons verified in the local face study

Inspect the installed MPFB version and service implementation before using internal APIs. The tested version was MPFB 2.0.18; do not pin future projects to it or assume the same extension module prefix on every install.

In that version, `TargetService.load_target()` creates a new shape key even when a matching target exists. Repeated calls can stack duplicate deformations. Set the existing key's value when present; otherwise load the target. For example, once `T`, `head`, and a verified target path are established:

```python
name = T.filename_to_shapekey_name(str(target_path))
key = head.data.shape_keys.key_blocks.get(name)
if key is None:
    key = T.load_target(head, str(target_path), weight=weight)
else:
    key.value = weight
assert abs(key.value - weight) < 1e-5
```

Investigate existing duplicate keys before removing any: preserve deliberate manual shapes and repair only known generated duplicates. Repeating a target update should leave the target count and intended deformation unchanged. Also inspect opposing increase/decrease targets when results seem unexpectedly weak or exaggerated.

Store localized procedural sculpt offsets in a separate named relative shape key when practical. Refit attached assets after changing the head and verify actual eye/hair fit. Reacquire evaluated objects after asset import or dependency-graph changes rather than retaining stale evaluated references. Asset import may remove unused material datablocks, so obtain/create materials after import when required.

## Eyes, skin, and hair

- Respect eye texture alpha when it masks transparent cornea regions. Verify irises remain visible in rendered views, not just material previews.
- Use skin color variation, roughness, and restrained pore detail. Texture alone does not provide the larger wrinkles, folds, sag, and feature volumes required for a convincing older face.
- Establish the hair mass, hairline, part, crown coverage, temple coverage, and nape silhouette before individual strands. Fine curves cannot rescue a wrong underlying hairstyle.
- A fitted free hair mesh plus surface-following curves can provide an editable starting point. Check transparency masks when placing strands so they do not appear on invisible hair-card regions or cross the forehead unintentionally.
- Inspect the profile and back as well as the front: disconnected bands, floating locks, glossy solid hair, and smooth uncovered nape patches can disappear in one favored view.

These techniques produced an editable likeness study, not a validated fully automatic photorealistic reconstruction system. Further progress may require direct sculpting and careful grooming rather than more global parameter changes.

## Focused references

- [MPFB extension](https://extensions.blender.org/add-ons/mpfb/) and [official script samples](https://github.com/makehumancommunity/mpfb2/tree/master/script_samples).
- [MakeHuman system assets](https://static.makehumancommunity.org/assets/assetpacks/makehuman_system_assets.html): verify the license of the selected asset; the previously used system skin, eye, and short02 hair assets were CC0. Add-on code licensing is separate.
- [CG Boost / Jim Morren realistic head lesson](https://www.youtube.com/watch?v=BPAvvF8py1M): manual blockout and feature sculpting.
- [Blender Studio realistic human research](https://studio.blender.org/training/realistic-human-research/): design, base meshes, retopology, and facial shape considerations.

Consult only the material needed for the current problem; do not claim to have watched a video from its title or description.
