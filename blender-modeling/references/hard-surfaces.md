# Props, vehicles, and manufactured objects

## From references to editable geometry

Establish consistent longitudinal, width, and vertical axes before modeling. Derive part placement from shared dimensions instead of independent guessed coordinates. For a toy car, useful parameters are overall length/width/height, wheelbase, track width, wheel radius/width, ride height, hood length, and cabin position. Estimate missing dimensions and label them as estimates.

Separate the body shell, cabin/glazing, wheel assemblies, lights, bumpers, and trim when those divisions aid editing. Start a curved body with a low-resolution cage or a sequence of cross sections. Use symmetry where the real object is symmetric. Bevels and subdivision can round manufactured forms, but inspect whether they shrink the silhouette or distort openings.

Repeated wheels should derive from the same wheel geometry and axle positions. Reuse mesh data or instances where independent geometry is unnecessary. Set origins and local axes for the intended edits or motion; avoid blanket origin/transform changes that disrupt working modifiers or animation.

## Assembly checks that matter

- Compare front, side, top, and three-quarter silhouettes before adding tiny seams or tread detail.
- Check wheel-to-body clearance, axle alignment, ground contact, cabin proportions, and symmetry using the evaluated result.
- A bounding-box overlap is a coarse diagnostic; it does not prove surface contact, connected topology, or a printable union. Judge intended contacts accordingly.
- Use actual thickness for shells that need it. A plane with a convincing material is not a solid printable window or body.
- Keep assembly seams when they represent real separate parts. Join or boolean-union only when the requested deliverable needs it.
- Match the material represented by the reference: molded plastic, painted die-cast metal, rubber, and glass have different roughness and edge treatment. Avoid using dramatic lighting to hide a poor shape match.

For one-view references, prioritize the observed view while checking that the inferred sides remain plausible. State which details were invented. A toy with exaggerated proportions should match the toy, not an idealized full-size car.

Use Blender's installed API and version-matched manual for modifier/operator details. No paid vehicle generator or asset service is a prerequisite.
