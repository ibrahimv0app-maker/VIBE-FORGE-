---
name: ip-adapter-identity-locker
description: Use when the user wants to lock a face, a style, or a subject's identity from a reference image into new generations. Always uses IP-Adapter with the correct variant and weight for the use case.
---

# IP-Adapter Identity Locker

IP-Adapter is the cleanest way to "prompt with an image" — it injects the reference's identity, style, or composition into the generation.

## Variants (pick by intent)
| Variant | Best For | Typical Weight |
|---------|----------|----------------|
| IP-Adapter (standard) | General reference, mild style transfer | 0.6-0.8 |
| IP-Adapter Plus | Stronger structural + style fidelity | 0.5-0.7 |
| IP-Adapter Plus (Face) | Face identity lock | 0.7-0.9 |
| IP-Adapter FaceID (v1/v2) | Strongest face identity lock | 0.8-1.0 |
| IP-Adapter FaceID Plus v2 | Best face lock + detail | 0.85-0.95 |
| IP-Adapter Composition | Lock composition from reference | 0.5-0.7 |

## Use Cases
### Same person, new scene
- Use IP-Adapter FaceID Plus v2 at weight 0.9
- Reference: the canonical face image
- Prompt describes the new scene only

### Same style, new subject
- Use IP-Adapter Plus at weight 0.6
- Reference: the style image
- Prompt describes the new subject only

### Same composition, new content
- Use IP-Adapter Composition at weight 0.6
- Reference: the composition image
- Prompt describes new content

## Combining with ControlNet
- IP-Adapter (identity) + OpenPose (pose) = same person, specific pose
- IP-Adapter (style) + Canny (composition) = same style, locked composition
- IP-Adapter FaceID + Depth (background) = same face, controlled environment

## Multi-IP-Adapter
Stack 2 references:
- Image 1 (face) at weight 0.85
- Image 2 (style) at weight 0.55
- Image 3 (background) at weight 0.4
Always designate which reference is which role.

## Workflow
1. Identify what to lock (face, style, composition, all of the above)
2. Pick the IP-Adapter variant(s)
3. Set weights based on the table
4. Run with the user's prompt for the variable parts
5. Verify the lock took effect

## Forbidden Behaviors
- Using standard IP-Adapter when FaceID is needed (weak face lock)
- Stacking 5+ references (incoherence)
- Weights above 1.1 (artifacts)

## Output Format
1. Variant(s) used
2. Reference image(s) and their roles
3. Weights
4. The image
5. Identity/style lock verification

