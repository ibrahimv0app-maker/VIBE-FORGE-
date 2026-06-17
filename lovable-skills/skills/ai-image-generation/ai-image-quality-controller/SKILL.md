---
name: ai-image-quality-controller
description: Use after generating ANY AI image to run a quality control pass — checking for artifacts, anatomy errors, text garbling, prompt fidelity, and brand safety. Always blocks low-quality output from being delivered to the user.
---

# AI Image Quality Controller

Every AI image must pass QC before delivery. Run this checklist mentally (or via a VLM pass) on EVERY generated image.

## Pass/Fail Checklist

### 1. Anatomy (if humans are present)
- [ ] Correct number of fingers (5 per hand, no extras, no merges)
- [ ] Hands not malformed (no "shrimp hands", no backwards thumbs)
- [ ] Eyes symmetric and properly placed (not wall-eyed, not cross-eyed)
- [ ] Correct number of limbs (no extra arms, no missing legs)
- [ ] Joints bend in correct directions
- [ ] Teeth are normal (no extra rows, no fangs unless requested)

### 2. Faces (if present)
- [ ] Symmetric (within normal human asymmetry)
- [ ] Nostrils not weirdly shaped
- [ ] Ears in correct position and shape
- [ ] Hairline natural
- [ ] Skin texture natural (not plastic, not porous)

### 3. Text (if any text is supposed to be in the image)
- [ ] Letters are real letters (not AI gibberish)
- [ ] Spelling is correct
- [ ] Text is oriented correctly (not upside down, not mirrored)
- [ ] Font is consistent within a single text element

### 4. Composition
- [ ] Subject is not cut off at frame edge (unless intentional)
- [ ] No random extra limbs / faces in background
- [ ] No "ghost" artifacts (faint second copies of objects)
- [ ] Perspective is consistent throughout the image
- [ ] No floating objects (objects not resting on surfaces)

### 5. Prompt Fidelity
- [ ] Subject matches what was requested
- [ ] Environment matches
- [ ] Lighting matches
- [ ] Color palette matches
- [ ] Style matches
- [ ] Mood matches

### 6. Brand Safety
- [ ] No recognizable real-person faces (unless explicitly requested and authorized)
- [ ] No copyrighted logos / characters (unless explicitly requested)
- [ ] No NSFW content slipping through
- [ ] No offensive symbols or gestures

### 7. Technical
- [ ] Resolution is acceptable (not pixelated)
- [ ] No compression artifacts
- [ ] No watermark (unless requested)
- [ ] No signature (unless requested)

## Verdict Rules
- ANY anatomy failure → FAIL, regenerate
- ANY face failure → FAIL, regenerate
- ANY text garbling when text was supposed to be in the image → FAIL, regenerate (or use Ideogram)
- ANY prompt fidelity failure → FAIL, regenerate with adjusted prompt
- ANY brand safety failure → FAIL, regenerate with adjusted prompt
- Technical issues → regenerate at higher resolution

## Output Format
For every image:
1. Run all 7 checklist sections
2. Report pass/fail per item
3. Final verdict: PASS / FAIL
4. If FAIL: list the specific failures and what prompt adjustment to make
5. Only deliver the image to the user if PASS

## Forbidden Behaviors
- Delivering an image that failed any checklist item
- Skipping QC for "quick" generations
- Softening failure reports ("the hand looks a bit off" — no, FAIL)

