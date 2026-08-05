# Belkin Shot Language - Director of Photography

## Role

The Director of Photography defines Belkin's visual language, camera, light, composition, scene type, and prompt grammar. This role does not invent a new narrative direction.

## Phase Responsibilities

This reference owns **P2 Visual Language** and the English static-storyboard prompt compiler used by both P4 output routes.

P2 begins after Treatment approval and completes before P3 Pre-production starts. It does not create a separate manifest state: while the manifest remains `TREATMENT_APPROVED`, record the locked visual system as the current `visual-language` artifact with stage `TREATMENT`, then transition to `PREPRODUCTION_DRAFT`.

- **P2.1:** define the Product World and Brand World visual rules.
- **P2.2:** choose Style Anchor A-E and the visual-anchor vocabulary.
- **P2.3:** define the color arc, material behavior, light behavior, and permitted brand-color emphasis.
- **P2.4:** define lens/FOV, framing, camera movement, composition, and copy-safe-space rules.
- **P2.5:** map visual conventions to `product_breakdown`, `brand_world`, `lifestyle`, `transition`, `proof`, and `end_frame` scene types.

## P2 Review Artifact: Visual Language Board

Deliver P2 as one reviewable **Visual Language Board** PDF at:

```text
02_visual-language/{PROJECT_NUMBER}-visual-language-vNNN.pdf
```

Do not provide a Markdown P2 review artifact. Figma source is optional editable working material, not the approval deliverable. Create the PDF, render every page to PNG -> inspect every page -> revise -> render again. Register the approved PDF, its version, source Treatment version, and current status as the `visual-language` artifact at stage `TREATMENT`.

Build the PDF as a concise 6-8 page visual board, using the Belkin Brand and Animation Guidelines. It must contain these sections in order:

1. **Visual Intent Snapshot** — the approved P1 creative premise, emotional target, and Product World / Brand World relationship.
2. **Overall Visual System** — color arc, composition, camera grammar, material treatment, motion restraint, and brand-color emphasis.
3. **CG World** — studio-light environment, background depth or tonal gradient, reflection behavior, camera language, and allowed effects. Never use a pure solid or empty negative-fill CG background.
4. **Lifestyle World** — environment, daylight or practical-light logic, human behavior, product hierarchy, and camera observation.
5. **Moodboard & Reference Analysis** — embed or clearly place each supplied visual reference as `VR##`; record its source and the usable findings for light, palette, camera, composition, material, and effects. Do not invent an unavailable reference image.
6. **Scene-style Mapping** — assign the approved visual system to `product_breakdown`, `brand_world`, `lifestyle`, `transition`, `proof`, and `end_frame` scenes.
7. **Handoff Locks** — list P3/P4 rules that must be inherited and every remaining visual input that prevents a lock.

P2 validates the overall visual world; it does not approve final product, cast, location, prop, device, or shot-specific locks. P3 uses the approved Visual Language Board PDF as its visual source of truth; P4 applies it shot by shot without re-opening the visual direction.

## Static Storyboard Prompt Compiler

Shot Language is the single authority for static-storyboard image prompts. Read and apply this contract whenever P4 selects `IMAGEGEN` or `EXTERNAL_PROMPTS`; the Director supplies approved source locks and route-specific delivery only.

Use the approved shortlist Description, Shot size, and Camera movement together with P2 Visual Language, P3 Pre-production, approved reference assets, and the approved production method. Generate one fluent English paragraph per stable Shot ID. It describes one static storyboard image, never a timed camera path or multi-phase sequence.

### Prompt Output

```yaml
prompt_language: "en-US"
prompt_type: "static_storyboard_image"
prompt: "[Quality Anchor] + [Subject Description] + [Environment / Space] + [Lighting] + [Composition / Camera] + [Style Anchor]. Constraints: ..."
source_locks:
  - approved P2 Visual Language
  - approved P3 Pre-production
  - approved shortlist row
```

### Six-Layer English Assembly

Use this exact creative order:

```text
Quality Anchor -> Subject Description -> Environment / Space -> Lighting -> Composition / Camera -> Style Anchor
```

1. **Quality Anchor** — place first. Use the approved production method and P2 style: `live-action cinematic photography, natural skin texture, realistic daylight response`; `high-end photoreal CG, cinematic product lighting, physically credible material response`; or `high-resolution cinematic photography, premium lens rendering, restrained filmic color grade`. Do not assert an unsupported engine, resolution, skin behavior, or visual effect.
2. **Subject Description** — for people, use approved role or identity, body type, facial traits, wardrobe, pose or action, then expression or emotion. For a product or object, use type, approved material, supported scale or proportion, approved surface effect, and visible state. Keep geometry, ports, logo, UI, cables, and claims reference-locked.
3. **Environment / Space** — describe spatial type, perceived scale, materials or surfaces, atmosphere, and specific P3 set details. Do not substitute a generic location or invent clutter.
4. **Lighting** — describe exposure, key-light position and source, shadow or reflection behavior, and color temperature or color relationship. For CG, use a dimensional studio-light field, floor plane, gradient, or equivalent tonal depth.
5. **Composition / Camera** — describe shot size, camera height and angle, approved lens or FOV, subject hierarchy, depth, and copy-safe space. Convert motion into one still moment: `the frame resolves during a gentle push-in`. Do not ask the model to execute timed movement.
6. **Style Anchor** — close with the approved P2 style anchor, visual-language vocabulary, color arc, moodboard findings, and material or camera constraints. Do not create a new visual direction.

### Constraints Tail

After the six creative layers, append one concise `Constraints:` sentence. State the required reference assets, reference-supported product state, static-image-only behavior, compositing-only UI/logo/CTA/claim elements, negative constraints, and any shot-specific production-method warning. This tail protects production truth; it is not a seventh visual layer.

For CG, never use a pure solid or empty negative-fill background. Do not invent material, LED, screen, port, cable, UI, logo, claim, CTA, legal copy, or unsupported product behavior.

`EXTERNAL_PROMPTS` writes this English static prompt to the Markdown `Prompt` column. `IMAGEGEN` uses the same compiled prompt for its 16:9 planning reference and records its prompt version against the Shot ID. This compiler does not automatically produce Seedance or other video prompts.

## Belkin Visual System

Default aesthetic: **Calm technology** - precise, human, useful, quietly premium, and physically believable.

### Product World

Controlled studio or CG, accurate product geometry, material response, edge light, negative fill, macro detail, and product-led composition.

### Brand World

Recognizable everyday environments, natural human behavior, believable device relationships, and product integrated into the user's action.

## Style Anchor System

- A - Live-action cinematic
- B - Cinematic drama
- C - Stylized CG
- D - High-end product CG
- E - Lifestyle editorial

Choose one dominant anchor and explain why it fits the Belkin category.

## Scene Types

| Scene type | Visual requirement |
|---|---|
| product_breakdown | macro detail, product state, material behavior, hero progression |
| brand_world | environment carrier, user action, product role, transition out |
| lifestyle | natural product visibility, user continuity, motivated camera reveal |
| transition | match-cut source and target, movement or texture continuity |
| proof | clear benefit evidence, approved product behavior, risk mitigation |
| end_frame | product placement, copy-safe space, approved overlay space |

## Camera and Light Rules

- A camera move must reveal, follow, contrast, or escalate product meaning.
- Use macro for texture and industrial design; medium for behavior; wide for world and relationship.
- Define lens/FOV, camera height, movement speed, and product orientation when accuracy matters.
- Define light source direction, edge separation, reflection behavior, and color transition.
- Do not invent material, LED, screen, port, cable, or UI behavior.

## Color Arc and Match Cut

Every storyboard sequence records:

```yaml
color_arc: "neutral start -> functional accent -> emotional shift -> end frame"
match_cut: "shape | movement | color | light | texture | continuity | hard_cut"
camera_intent: "one dominant camera idea"
material_behavior: "reference-supported surface behavior"
```
