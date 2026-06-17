---
name: controlnet-composition-locker
description: Use when the user wants to lock the composition of an AI image to a specific structure — a sketch, a depth map, a pose, an edge map. Always uses ControlNet to enforce the structural constraint.
---

# ControlNet Composition Locker

ControlNet is the scalpel of AI image generation — it lets you lock structure while varying style.

## ControlNet Types (pick by intent)
| Type | Locks | Best For |
|------|-------|----------|
| Canny | Edges | Line-art-to-rendered, composition lock |
| Depth | Depth map | Foreground/background separation, spatial lock |
| OpenPose | Body skeleton | Character pose lock |
| MLSD | Straight lines | Architecture, interiors |
| SoftEdge | Soft edges | Painterly composition lock |
| Scribble | Rough sketch | Sketch-to-rendered |
| Tile | Overall structure | Style transfer while keeping composition |
| Inpaint | Mask region | Local edits |
| IP-Adapter | Image prompt | Style or identity transfer |
| Reference | Whole image | Looser reference |

## Weights
- ControlNet weight 0.5-0.7: structural guidance, allows some variation
- ControlNet weight 0.8-1.0: hard structural lock
- ControlNet weight 1.0+: extreme lock (often causes artifacts)

## Multi-ControlNet
Stack 2-3 ControlNets for combined constraints:
- OpenPose (weight 0.8) + Canny (weight 0.5): pose lock + composition lock
- Depth (weight 0.7) + IP-Adapter (weight 0.6): spatial lock + style reference
- Canny (weight 0.6) + Tile (weight 0.5): edge lock + structural lock

## Starting Image
- For OpenPose: provide or generate a pose skeleton
- For Canny: provide a line drawing or extract edges from a reference
- For Depth: provide a depth map (or generate one from a reference)
- For Scribble: any rough sketch works

## Workflow
1. Identify what to lock (pose, edges, depth, structure)
2. Pick the ControlNet type that locks it
3. Prepare the conditioning image (sketch / pose / depth map)
4. Set ControlNet weight based on how strict the lock should be
5. Run with the user's style prompt
6. Verify the locked structure is preserved

## Forbidden Behaviors
- Using ControlNet weight above 1.2 (artifacts)
- Stacking more than 3 ControlNets (coherence collapse)
- Forgetting to verify the structural lock took effect

## Output Format
1. ControlNet type(s) used and why
2. Conditioning image (sketch / pose / depth)
3. Weights
4. The image
5. Lock verification

