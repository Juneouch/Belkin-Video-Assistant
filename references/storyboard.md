# Belkin Storyboard - Director

## Role

The Director translates the approved Treatment, Shot Language, and Pre-production package into one Markdown-first Storyboard / Shotlist stage, then into either ImageGen planning references or an external still-image prompt handoff.

## Director Handoff

Read in this order:

1. Approved `treatment.md` output.
2. Approved 16:9 P3 Pre-production PDF package.
3. Approved P2 Visual Language Board PDF and its `shot-language.md` visual-system contract.
4. Product reference assets and approved UI / claims.

Do not silently change the creative direction, category strategy, or brand world.

## Phase Responsibilities

This reference owns **P4 Unified Storyboard / Shotlist**. It uses only the existing `SHOTLIST_DRAFT`, `SHOTLIST_REVIEW`, and `SHOTLIST_APPROVED` states.

- **P4.1:** declare the TVC story density, then write the one- or two-sentence Video Spine: continuous camera language, product-state change, and motivated transition logic.
- **P4.2:** create the first review artifact as a versioned Markdown shortlist with stable Shot IDs and the seven required primary columns.
- **P4.3:** apply the approved Lifestyle Film, Integration of Animation and Lifestyle, or Cinematic Animation format; map each primary USP or key feature to truthful visual proof.
- **P4.4:** obtain shortlist approval, then record one `IMAGEGEN` or `EXTERNAL_PROMPTS` output route without creating a new state.
- **P4.5:** for `IMAGEGEN`, create and review one 16:9 planning reference per stable Shot ID after P3 approval; for `EXTERNAL_PROMPTS`, append English static still prompts to a new version of the same shortlist.
- **P4.6:** create the canonical V2 shotlist only after the selected route is complete. It remains the structured source of truth for timing, references, constraints, and route traceability.

## Initial Markdown Shortlist

At `SHOTLIST_DRAFT`, first declare the story density and provide the Video Spine, then create:

```text
05_storyboard/{PROJECT_NUMBER}-shortlist-vNNN.md
```

Use this exact primary table:

| Shot number | Duration | Description | Shot size | Camera level | Camera movement | VO |
| --- | --- | --- | --- | --- | --- | --- |

`Camera level` is required for every row. Use one controlled vertical viewpoint: `eye-level`, `low angle`, `high angle`, `top-down`, `ground-level`, or `over-the-shoulder`. Vary it deliberately across the sequence to support the Video Spine; do not default every frame to eye level.

### Video Spine First

Write a **Video Spine** in one or two sentences before any per-shot Description. It is the time-axis cause-and-effect chain: how camera grammar continues, how the product state changes, and how every beat connects to the next.

The Video Spine is not a one-take requirement. Use hard cuts, match cuts, dissolves, jump cuts, or other transitions when they are motivated and the sequence still has a clear temporal position for every frame.

Treat the storyboard grid as a frozen version of the Video Spine and a later video prompt as its expanded version. They grow from the same sequence logic; never create disconnected stills first and attempt to invent video continuity afterward.

The Video Spine is a writing and continuity step, not static-image prompt text. Store it as a continuity or video-flow note for downstream video prompting. Do not insert it into the static storyboard prompt body or its Quality, Subject, Environment, Lighting, Composition, and Style layers.

### Story Density

Declare one density for every TVC storyboard:

- **LOW (default) — visual-driven:** there may be no narrative arc, but there must be a Video Spine. Camera grammar, light progression, and product-state transformation create the time flow. Start every Description with `[Shot size · Camera level]`, then specify the product angle, visual hierarchy, light, and frame intent precisely.
- **MEDIUM — scene progression:** a journey, use case, or process progresses across the frames while each frame remains a controlled commercial composition. Write one short journey line before the rows. The `Camera level` column remains required; the inline Description prefix is optional.
- **HIGH — not permitted for TVC:** do not use a high-density narrative mode or delegate framing decisions to AI. Belkin TVC frames require deliberate composition, shot size, camera level, light, and product presentation.

Low and medium density obey the same Video Spine principle. A low-density film without a conventional story still needs time flow through camera, light, product state, and transitions.

Use stable Shot IDs (`S01`, `S02`, …). Durations must be continuous and sum to the approved runtime. When no VO line is approved, write `—`; do not invent VO, claims, CTA, legal copy, readable UI, or logo artwork.

Description is a visual account of the frame and its change, not a production label. Include, where relevant:

- location, spatial environment, and set dressing;
- time of day, light source, contrast, and color behavior;
- visible person, styling, posture, and performance behavior;
- person-to-product interaction and the primary physical action;
- product state and only reference-supported product behavior;
- framing evolution or in-shot visual change; and
- incoming or outgoing visual continuity principle.

Every CG Description and static prompt uses a dimensional studio-light field, floor plane, gradient, or comparable tonal depth: never a pure solid or empty negative-fill background.

### Dynamic Effects: Static Result, Video Process

When a concept contains dynamic effects, use the storyboard grid to freeze one legible **result state** and reserve the full process for an explicitly requested video prompt. Do not force a multi-stage transformation into a single static frame.

| Dynamic concept | Static storyboard frame | Optional video prompt |
| --- | --- | --- |
| Liquid metal or particles form the product | Product is fully formed and resolved | Describe flow, convergence, contour reveal, material settling, and final formation |
| Product components float apart | Components are already separated in a clear exploded view | Describe controlled separation, suspension, and any connecting energy treatment |
| Screen turns on | Screen is already lit with the approved interface state | Describe the illumination, pixel, or interface reveal sequence |
| Liquid spill, water droplets, or a frozen person | Capture one physically legible frozen moment | Describe the action and complete physical progression over time |
| Paper or fragment storm | Fragments are visibly suspended in a resolved composition | Describe the onset, motion, suspension, and release or recovery |

Keep the frozen result reference-supported, physically credible, and consistent with the approved product, person, and location locks.

After every shortlist version, present the artifact and only:

```text
a. Approve
b. Provide feedback and revise
```

For revision, require:

```text
- Section: [shot ID or section name]
  - Change: [specific revision required]
```

Record feedback append-only; regenerate the affected shortlist version and return to the same review loop. Once the Markdown shortlist is approved, ask only:

```text
a. Enter storyboard-image generation
b. Add image prompts for external generation
```

Use the Shot Language static-storyboard prompt contract for both output routes.

## Storyboard Reference Images

Storyboard reference images are allowed only after P3 Pre-production is approved and the approved shortlist selects the `IMAGEGEN` route. Use the English static prompt compiled by Shot Language with the `imagegen` skill to create one 16:9 raster planning reference per stable Shot ID. The compiler receives the approved Description, Shot size, Camera level, Camera movement, P2 visual language, P3 product/character/location/prop/device/cable/UI locks, and approved production method. For each frame, record its Shot ID, path, prompt version, and source references in a versioned storyboard-reference index.

Present the full set together for approval. Frame-only feedback must name affected stable Shot IDs; regenerate only those frames, retain all unaffected paths, and re-present the set in `SHOTLIST_REVIEW`. Feedback that changes a shortlist Description, duration, camera field, or Video Spine reopens `SHOTLIST_DRAFT` and follows the shortlist review loop. These frames are not final product renders and do not authorize video, edited footage, or motion-media generation.

## External Still-Image Prompt Route

When the approved shortlist selects `EXTERNAL_PROMPTS`, append a `Prompt` column to a new version of that same Markdown file. Write one English static still-image prompt per Shot ID. Each prompt uses the Shot Language compiler, describes one static storyboard/keyframe moment, and preserves the approved Description, P2/P3 source locks, copy-safe space, product-accuracy constraints, compositing responsibilities, and negative constraints.

Do not automatically compile Seedance or other video prompts in this route. A video prompt may be written only after the user explicitly requests it.

## Storyboard Shot Contract

```yaml
shot_id: "S01"
scene_type: "product_breakdown | brand_world | lifestyle | transition | proof | end_frame"
timecode: "00:00-00:03"
purpose: "one dominant narrative purpose"
usp_or_key_feature: "approved USP or key feature demonstrated in this shot; empty only when the shot has no feature-proof role"
feature_story_function: "how the USP/key feature advances the story, user outcome, or proof"
framing: "shot size, angle, lens/FOV, composition"
camera_level: "eye-level | low angle | high angle | top-down | ground-level | over-the-shoulder"
camera_intent: "one dominant camera idea"
camera_movement: ""
product_state: "approved visible state"
subject_action: "one main action"
lighting_intent: "source direction, contrast, material response"
material_behavior: "reference-supported surface behavior"
color_arc: ""
match_cut: "shape | movement | color | light | texture | continuity | hard_cut"
required_assets: []
ai_feasibility: "low | medium | high | very_high"
negative_prompt: []
production_method: "live_action | CG | compositing | AI_storyboard_only"
```

At the shortlist level, also store:

```yaml
story_density: "LOW | MEDIUM"
video_spine: "one or two sentences; sequence continuity only, never static-prompt text"
```

## USP and Key-Feature Story Rule

Every storyboard MUST embed at least one approved USP or key feature into the story. Map each primary USP or key feature to a named story beat and visual proof; do not treat it as an isolated title card or an unsupported product claim. Use `usp_or_key_feature` and `feature_story_function` to show how the feature changes the situation, supports a user action, or makes the product benefit credible.

Only use claims and product behavior supported by the approved treatment and references. If a priority USP cannot be shown truthfully, flag it as an open production or compositing requirement rather than inventing an interaction.

## Lifestyle Film

Keep the product inside a lifestyle world and reveal it through user behavior, camera grammar, focus, and light. End with a concentrated Hero Shot.

## Integration of Animation and Lifestyle

Use animation to show product appearance and material, then use lifestyle footage to show the use scenario. Name the match cut or transition logic between the two worlds.

## Cinematic Animation

Use a controlled multi-phase product film: dark reveal -> material macro -> structure / feature proof -> functional state -> hero -> end frame. The product is the only protagonist. Every phase must define product state, camera intent, material behavior, light movement, and the relevant USP or key-feature proof. Use approved render, CG, or compositing for exact geometry and readable UI.

## Optional Video-Prompt Contract

Use this contract only when the user explicitly requests a separately scoped video-prompt package after the unified P4 route is complete. It does not run automatically and cannot alter approved product geometry, claims, Shot IDs, timing, or shot purpose.

```yaml
tool: "Seedance 2.0"
input_images: ["storyboard_grid", "product_multiview"]
audio: "no background music unless explicitly approved"
video_spine: "approved sequence continuity note"
phases:
  - phase_id: "P01"
    timecode: "00:00-00:04"
    scene_type: ""
    camera_intent: ""
    camera_movement: ""
    subject_action: ""
    product_state_change: ""
    lighting_change: ""
    match_cut_out: ""
    dynamic_effect_process: "required only when an approved dynamic effect needs motion over time"
    negative_prompt: []
```

## Director QA

- Shot IDs and timecodes are continuous and sum to the runtime.
- The initial review artifact is the seven-column Markdown shortlist with an approved Video Spine and declared `LOW` or `MEDIUM` density.
- Every row contains a controlled Camera level, and the sequence varies viewpoint intentionally where the Video Spine calls for it.
- Every Description contains the required visual context, truthful product behavior, and a motivated continuity rule where relevant.
- LOW-density Descriptions begin with `[Shot size · Camera level]`; MEDIUM-density boards include a journey line before their rows.
- Static boards freeze dynamic effects in one resolved state; only a separately requested video prompt describes the full effect process.
- `IMAGEGEN` canonical shots trace to a reviewed 16:9 planning reference; `EXTERNAL_PROMPTS` canonical shots trace to one English static still prompt.
- No Seedance or other video prompt exists unless it was explicitly requested after P4.
- Product is visible often enough to support the story, but not repeated without purpose.
- Product state, material, color, and cable behavior are reference-supported.
- Every primary USP or key feature has a named story beat, truthful visual proof, and a stated story function.
- Every transition has a match-cut logic or explicit hard-cut reason.
- High-risk interactions name the production method.
- End Frame exists with logo, CTA, and legal-copy space reserved for approved design/compositing.
