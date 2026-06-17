---
name: concept-art-pipeline
description: Use when generating concept art for games, films, or animation — characters, environments, props, vehicles, creatures. Always produces production-ready concept sheets with multiple angles and detail callouts.
---

# Concept Art Pipeline

Concept art is design communication, not finished illustration. It must convey: form, scale, material, function, and mood.

## Concept Sheet Anatomy
A proper concept sheet includes:
- Main hero view (the money shot)
- 1-2 alternate angles or poses
- Detail callouts (zoom-ins on key features, materials, mechanisms)
- Color / material swatches
- Scale reference (silhouette next to a human, if applicable)
- Optional: expression sheet (for characters) or variant sheet (for props)

## Prompt Template (Character)
```
Character concept sheet for [CHARACTER NAME], [role: hero / villain / NPC],
[full identity description], [outfit and gear with materials and colors],
multiple views: hero pose + side profile + back,
detail callouts: weapon, helmet, boots, fabric texture,
neutral gray background, flat studio lighting, full body,
digital painting, ArtStation quality, ultra-detailed, 4k
```

## Prompt Template (Environment)
```
Environment concept art for [LOCATION NAME], [biome / era / function],
[architectural style], [time of day and weather],
[scale anchor: small figure / vehicle for scale],
wide establishing shot, atmospheric perspective,
digital painting, cinematic, ArtStation quality, ultra-detailed, 4k
```

## Prompt Template (Prop / Vehicle)
```
Prop concept sheet for [OBJECT NAME], [function],
[material and color spec], [era / style],
hero view + side view + top view,
detail callouts: mechanism, material, wear pattern,
neutral gray background, studio lighting,
digital painting, ultra-detailed, 4k
```

## Design Coherence Rules
- Material choices must make sense for the function (no glass armor for a tank)
- Wear and tear must match the implied history
- Silhouette must be readable at thumbnail size
- Color palette must fit the project's art bible (ask if not provided)

## Iteration Protocol
1. Generate 3-4 silhouette thumbnails first
2. User picks 1-2 favorites
3. Develop those into full concept sheets
4. Generate variants of the chosen design (color, gear, expression)
5. Final pass: detail callouts and material swatches

## Forbidden Behaviors
- Single-image concepts without alternates
- Detail callouts that don't match the hero view
- Random props or details that have no narrative purpose

## Output Format
1. Concept statement (one paragraph)
2. The sheet
3. Material and color notes
4. Scale note

