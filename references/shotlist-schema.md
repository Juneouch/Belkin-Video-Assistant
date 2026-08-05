# Director Workbook Schema

## Belkin TVC Schema Extension

Use the following fields when the request is a TVC, brand film, cinematic product breakdown, brand-world crosscut, or lifestyle film. These fields extend the PDP shotlist; they do not replace the stable shot ID and product reference fields.

```yaml
shot_id: "S01"
scene_type: "product_breakdown | brand_world | lifestyle | transition | proof | end_frame"
product_category: "power_bank | charger | wireless_charger | cable | audio | dock_hub | adapter | screen_protector | switch_accessory | creator_accessory"
narrative_model: "stay_connected | remove_friction | follow_the_user | one_product_many_moments | chaos_to_control | invisible_infrastructure | personal_space | everyday_continuity"
brand_world: ""
product_state: "approved visible state; no invented behavior"
camera_intent: "one dominant camera idea"
lighting_intent: "source direction, contrast, material response"
material_behavior: "reference-supported surface behavior"
color_arc: "start -> functional accent -> emotional shift -> end frame"
match_cut: "shape | movement | color | light | texture | continuity | hard_cut"
ai_feasibility: "low | medium | high | very_high"
product_integration_naturalness: 1
required_reference_assets: []
negative_prompt: []
production_method: "live_action | CG | compositing | AI_storyboard_only"
```

## TVC Coverage Rules

- A product-breakdown sequence needs macro detail, product state, material behavior, and a clean hero.
- A brand-world crosscut needs a complete phase per world; do not switch locations inside a phase unless the treatment explicitly calls for it.
- A lifestyle sequence needs user behavior, product visibility, continuity, and a final Hero Shot.
- Every high-risk product interaction must name a safer method such as approved render, CG, live action, or compositing.
- Every TVC shotlist must include an `end_frame` shot and copy-safe space.

Use one row per shot. Keep IDs stable so the workbook, prompt pack, and generated images can be updated without breaking cross-references.

## Workbook sheets

### Shotlist

Recommended columns, in this order:

`Shot ID`, `Scene ID`, `Beat`, `Type`, `Time In`, `Time Out`, `Duration`, `Aspect / Crop`, `Shot Size`, `Angle / Height`, `Lens / FOV`, `Camera Movement`, `Composition`, `Action / Performance`, `Product Role`, `Feature / Proof`, `Character IDs`, `Location ID`, `Prop IDs`, `Lighting`, `Color / Mood`, `Material / Surface`, `Audio / SFX / VO`, `On-screen Copy`, `Edit / Transition`, `Prompt ID`, `Reference IDs`, `Status`, `Notes`

Use `Type` values such as `Hook`, `Context`, `Lifestyle`, `Proof`, `Macro`, `Transition`, `Hero`, `Packshot`, `Cutdown`, and `Optional`.

Write `Action / Performance` in present tense and `Camera Movement` as a motivated action: `slow push-in as the magnetic connector seats`, not just `dolly in`.

### Characters

`Character ID`, `Name / Role`, `Narrative Function`, `Age Range`, `Appearance`, `Wardrobe`, `Silhouette / Scale`, `Gesture Language`, `Performance Arc`, `Relationship to Product`, `Continuity Constraints`, `Reference IDs`, `Status`, `Notes`

### Locations

`Location ID`, `Name`, `Narrative Function`, `Spatial Description`, `Time / Weather`, `Architecture`, `Palette`, `Key Surfaces`, `Practical / Ambient Elements`, `Light Direction`, `Camera Access`, `Motion / Atmosphere`, `Continuity Constraints`, `Reference IDs`, `Status`, `Notes`

### Props

`Prop ID`, `Name`, `Narrative Function`, `Shot IDs`, `Interaction`, `State Before`, `State After`, `Color / Material`, `Scale / Placement`, `Continuity Constraints`, `Competes with Product?`, `Reference IDs`, `Status`, `Notes`

### Product

`Product ID / SKU`, `Variant`, `Approved Name`, `Hero Feature`, `Feature Proof`, `Silhouette / Hero Orientation`, `Color / Finish`, `Material Truth`, `Ports / Buttons / UI Truth`, `Reference Image IDs`, `Do Not Change`, `Claims / Legal Notes`, `Status`, `Notes`

### Prompt Pack

`Prompt ID`, `Shot ID`, `Frame Purpose`, `Product Lock`, `Character Lock`, `Location Lock`, `Prop Lock`, `Action`, `Composition`, `Camera`, `Lighting`, `Material`, `Mood / Valence`, `Arousal`, `Color`, `Continuity`, `Negative Prompt`, `Reference IDs`, `Image Path`, `Approval`, `Notes`

Assemble the final prompt in this order:

`[format and frame purpose] + [product lock] + [character/location/prop locks] + [specific action] + [composition and camera] + [lighting and material behavior] + [mood/color] + [continuity constraints] + [negative prompt]`.

### Storyboard Index

`Frame ID`, `Prompt ID`, `Shot ID`, `Scene ID`, `Image Path / Link`, `Aspect`, `Generation Version`, `Source References`, `Approval`, `Revision Note`, `Owner`, `Date`

## Prompt guardrails

Always lock product identity before style. Include reference-image IDs when the product has distinctive geometry, logo, port layout, or screen content. Describe one clear action per frame. State what is foreground, midground, and background. Specify the intended hero surface and how the light travels across it.

Default negative prompt additions:

`wrong product model, altered industrial design, extra ports, missing ports, incorrect logo, warped text, duplicate product, duplicate hands, extra fingers, floating objects, impossible cable connection, inconsistent wardrobe, inconsistent lighting direction, unreadable UI, blown highlights on the hero feature, muddy silhouette, cluttered background, watermark, generic substitute product`

## QA checklist

- Every `Shot ID` is unique and referenced consistently.
- Every shot has a beat, type, shot size, action, product role, and proof or purpose.
- Product claims and feature names match the source brief.
- Character, location, and prop IDs exist before they are referenced.
- Prompt IDs map one-to-one to selected storyboard frames.
- Hero and proof shots exist before optional mood shots.
- Essential meaning is visible or captionable with audio removed.
- `Time In` + `Duration` and `Time Out` are internally consistent.
- No prompt asks an image model to invent an unprovided product detail.
