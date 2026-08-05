# Belkin Pre-production - Production Team

## Role

The Production Team turns an approved Treatment into a controllable production package. It locks people, product presentation, locations, props, references, and continuity before storyboard generation.

## Phase Responsibilities

This reference owns **P3 Pre-production** after the Treatment is approved and the approved P2 Visual Language Board PDF has been recorded as the current `visual-language` artifact at stage `TREATMENT`. Use that PDF as the visual source of truth; do not reopen its visual direction inside the Pre-production package.

- **P3.1:** lock product grooming: SKU, variant, orientation, approved reference assets, and visible feature boundaries.
- **P3.2:** lock casting, appearance strategy, styling, wardrobe, gesture language, and product-interaction boundaries; generate the C01 Character Sheet reference.
- **P3.3:** create location-scout records with spatial logic, time of day, surfaces, practical lights, and camera access; generate the L01 Location Sheet reference.
- **P3.4:** lock props, device relationships, cable states, and safer methods for high-risk interactions.
- **P3.5:** create the stable asset register and cross-stage continuity constraints.

The P3 package must be explicitly `APPROVED` before P4 Storyboard and Video Script begins.

## P3 Reference Requirements and Review

Before creating the final package, declare the applicable `reference_requirements` from the approved Treatment and P2 Visual Language Board:

- `character`: required only when a visible person, partial body, silhouette, or hands-only interaction appears in the approved story.
- `location`: required only when a real-world location appears and needs an environmental continuity lock.
- `[]`: valid for a controlled Pure CG product world with no visible person or real-world location.

Generate, render, and inspect only the required ImageGen planning references. `PREPRODUCTION_REFERENCES` approves the applicable set under one `reference_pair_id`; it never requires an invented C01 or L01.

### C01 - Character Sheet

- Age, gender, career (optional), and outfit must come from the approved Treatment person definition. Use the Treatment's full person priority: age, gender, race/ethnicity, career, outfit/styling, then skin/hair direction.
- 16:9 2K image. Use a pure plain mid-grey `#D9D9D9` background.
- Use three equal vertical panels: left full-body front view, center full-body back view, right close-up headshot. Add a very faint soft floor-contact shadow beneath the two full-body views only.
- Use Soft, even, neutral studio lighting with consistent exposure and low contrast.
- Require a photorealistic professional character-sheet presentation, one consistent identity, natural anatomy, accurate front/back continuity, equal panel widths, centred compositions, and generous margins.
- Do not include text, labels, logos, watermarks, dramatic environment, extra characters, handheld props, duplicated limbs, or outfit changes.

### L01 - Location Sheet

- Derive the complete environment, time of day, and lighting from the approved Treatment and P2 locks.
- Make the location globally legible, with a Europe/United States production context. Avoid place-specific signage, stereotypes, or regional cues that limit the scene to one market.
- Full view of the whole environment; use an eye-level 3/4 angle rather than a detail crop.
- Use cinematic lighting, gentle warm shadows, soft bokeh, and fine 35mm film grain.
- For an interior, require lifestyle set dressing and a lived-in practical location. Use a desk lamp, bookcase, and a controlled selection of books to create a credible home-office atmosphere.
- When an approved location setup specifies tabletop practicals, show only those locked elements and leave the remaining work surface clear. For the WCH026 US home office, this means one unbranded IKEA-style desk lamp and one flush-mounted recessed power outlet on the walnut tabletop; do not add product, devices, cables, or unrelated desktop props.
- Do not include people, text, logos, watermarks, or generated UI.

If Treatment/P2 lacks a required person, location, time, or lighting detail, add the standard Attention - Input required callout and do not generate the affected image. Do not invent the missing attribute. The missing input does not block the Pre-production PDF review package: retain the callout and an explicit asset placeholder. It does block any P4 frame that depends on that TBD lock.

Register every required reference with a stable asset ID, prompt version, Treatment/P2 source versions, `reference_pair_id`, `generation_source: imagegen`, and `UNAPPROVED` review status. Present the required reference set together and show only:

```text
a. Approve
b. Provide feedback and revise
```

On approval, append `PREPRODUCTION_REFERENCES` through `project_controller.py` with the approved `reference_requirements`. This decision retains `PREPRODUCTION_DRAFT`. On feedback, require the standard bullet feedback contract and regenerate only the affected image, then present the applicable reference set again. When `reference_requirements` is empty, skip this image-review event and retain the explicit Pure CG/no-reference rationale in the package.

## Required Review Artifact: 16:9 PDF

Create the final Pre-production review package after every required reference is approved, or immediately when `reference_requirements` is empty:

```text
04_preproduction/{PROJECT_NUMBER}-preproduction-vNNN.pdf
```

Do not provide a Markdown or DOCX pre-production review artifact. Use the PDF skill to create a 16:9 PDF at 1920 x 1080, then render every page to PNG -> inspect every page -> revise -> render again before delivery.

Use this PDF page order with clear title hierarchy, lists, and fixed-geometry tables:

1. Cover, project metadata, approval status, and Contents
2. Pre-production Package
3. Character Sheet
4. Location Sheet
5. Prop Sheet

Embed available approved product, character, location, and prop reference images in their matching sections. Embed only the approved C01/L01 generated images. Label every image with its stable Asset ID, source path, prompt version, and source-version trace. When an image cannot be embedded, retain its source path and a clear placeholder; do not invent a replacement.

### Belkin document visual system

- Belkin Green `#6FFB38`: section accents, thin rules, and priority/status emphasis.
- Belkin Black `#000000`: title, headings, and primary text hierarchy.
- Belkin Gray `#F4F4F4`: table headers, information blocks, and secondary surfaces.
- Belkin White `#FFFFFF`: page background.
- Belkin Yellow `#F4D771`: only for missing-input Attention callouts.
- Prefer Suisse Int'l Book/Semibold. Use Inter when Suisse is unavailable.

Place missing-input callouts beside the affected section and summarize them near the beginning of the package. Use this exact structure:

```text
⚠ Attention — Input required
Section: [affected section]
Please provide: [specific material]
Accepted formats: [file/image/PDF/reference requirements]
Status: TBD - asset required
Impact: [what cannot be locked without it]
```

Do not ask the user to define logo placement or ending-card safe-zone dimensions. Derive them from the Belkin Brand and Animation Guidelines: use a black or white Belkin wordmark only, preserve at least half the height of the `l` as clear space, and apply the platform safe-zone rule. When the 1920x1080 animation-guideline layout applies, use the guideline's black 200 x 52 px logo at 125 px from the left and 100 px from the top. Treat final logo, CTA, claims, and UI as approved design/compositing responsibilities, not generated document or media content.

## Required Handoff

The Treatment must be `APPROVED` and include product category, narrative mode, brand world, appearance strategy, phases, and open approvals.

## Casting and Styling

Record `casting_and_styling` for every person appearing:

```yaml
character_id: "C01"
role_in_story: ""
age_range: ""
appearance: ""
wardrobe: ""
color_palette: ""
gesture_language: ""
product_interaction: ""
continuity_constraints: []
```

Use hands, partial body, silhouette, or no person when the product is the main subject. Never invent an identifiable person, cultural context, or wardrobe requirement as an approved fact.

## Product Grooming

The product lock must include:

```yaml
product_grooming:
  sku: ""
  variant: ""
  approved_reference_assets: []
  approved_hero_asset_id: ""
  approved_hero_image_path: ""
  approved_wordmark_path: ""
  hero_orientation: ""
  visible_features: []
  material_and_color: "reference-supported"
  cable_and_device_state: ""
  logo_and_ui: "approved design or compositing"
  unverified_details: []
```

Do not retouch, recolor, reshape, add ports, add lights, or change cable behavior without an approved source.
`approved_hero_asset_id`, `approved_hero_image_path`, and `approved_wordmark_path` are mandatory P3 locks for a client proposal deck. They select the exact approved colourway, image, and official wordmark used in P6; input-folder ordering and typeset substitute logos are never valid selection rules.

## Location Scout

For every world, record:

```yaml
location_scout:
  location_id: "L01"
  world: "product_world | brand_world"
  primary_location: ""
  time_of_day: ""
  architecture_and_spatial_logic: ""
  surface_and_materials: ""
  practical_lights: []
  camera_access: ""
  negative_space_for_product: ""
  continuity_constraints: []
```

Default category worlds are assumptions until approved: power bank = commute/travel; wireless charger = desk/bedside; audio = street/transit/bedroom; dock/hub = desk/studio; Switch = living room/travel; creator accessories = filming or podcast setup.

## Asset Consistency

```yaml
asset_consistency: "one register, stable IDs, approved source paths, and cross-stage reuse"
```

Maintain one asset register for product, character, location, prop, UI, logo, and reference images. Assign stable IDs and reuse them in storyboard and prompts.

```yaml
asset_id: "P01"
asset_type: "product | character | location | prop | ui | logo | generation-reference"
source_path: ""
approved_status: "DRAFT | APPROVED | REJECTED"
prompt_version: ""
source_treatment_version: ""
source_visual_language_version: ""
reference_pair_id: ""
used_in: []
continuity_notes: ""
```

## Pre-production QA

- Product references correspond to the SKU and variant.
- Character appearance and wardrobe remain consistent.
- Location supports the product category and narrative model.
- Props do not imply unsupported compatibility or claims.
- Every high-risk interaction has a safer method: approved render, CG, live action, or compositing.
- All unverified details are explicitly listed before storyboard work.
