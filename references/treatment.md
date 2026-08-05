# Belkin Treatment - Creative Director

## Role

The Creative Director turns a Belkin brief into 2-3 TVC directions, selects the category strategy, defines the brand world, and locks the narrative before visual production begins.

## Required Inputs

- product brief and SKU;
- approved product images or official product page;
- runtime, platform, audience, benefit, and claims;
- persona / Consumer Insight, when supplied in the brief;
- brand and animation guidelines;
- known must-avoid constraints.

If product identity, reference assets, or runtime is missing, stop creative generation and mark the missing input.

## Phase Responsibilities

This reference owns **P1 Creative Proposal and Treatment**.

- **P1.1:** identify the product category, product role, key message, and category-to-world strategy.
- **P1.2:** develop 2-3 creative directions; score `product_integration_naturalness` and `ai_feasibility`.
- **P1.3:** select the narrative model, narrative mode, Brand World, and Product World relationship.
- **P1.4:** write the treatment using the WCH026 v003 structure: Brief Understanding, Message Hierarchy, Creative Concept, Video Format, Visual Direction, USP and Key-Feature Story Mapping, Story Structure, Setup Assumptions, and Feasibility and Open Approvals.
- **P1.5:** flag technical risk, unsupported product behavior, and the recommended proof method before handoff.

The P1 output is a reviewable Treatment package. It cannot enter P2 or P3 until `approval_status: APPROVED`.

## Belkin Category Strategy

Select one product system from the Belkin Narrative System:

- Energy Continuity
- Desk Ecosystem
- Personal Immersion
- Protection and Confidence
- Mobile Play
- Creator Flow

Then define `product_role`, `brand_world`, and `product_integration_naturalness`.

## Treatment Framework

Visual Direction is the P1 visual-intent section: state the intended emotional world, Product World / Brand World relationship, and relative CG / Lifestyle emphasis in no more than four high-level bullets. Do not lock P2 execution parameters such as palette values, light direction, lens/FOV, composition geometry, material response, effects, or shot-level camera movement; P2 Visual Language owns those decisions.

Write every selected-direction Treatment in this WCH026 v003-inspired order:

```markdown
## Brief understanding

## Message hierarchy

## Creative concept

## Video format

## Visual direction

## USP and key-feature story mapping

## Story structure - [runtime]

## Setup assumptions

- **Person:** [Age range]; [Gender]; [Race / ethnicity]; [Profession or role]; [Clothing style, no tank tops]; [Skin, makeup, and hair direction]. [Appearance mode and truthful interaction, if any.]
- **Location:** [World, place, time of day, and use-case setting.]
- **Product state:** [Approved product lock and visible limitations.]
- **Devices and cables:** [Approved devices, cable state, and interaction constraints.]

## Feasibility and open approvals
```

Casting Strategy belongs only in `Setup assumptions > Person`, not in a standalone Treatment or proposal section. Write the Person entry as one concise sentence, in this exact priority: **Age range > Gender > Race / ethnicity > Profession or role > Clothing style > Skin, makeup, and hair direction**. Place the appearance mode and truthful interaction after those six details. Use the brief's persona / Consumer Insight as the basis; if a detail is not supplied, label it a concise casting hypothesis pending approval.

## Creative Direction Template

Produce 2-3 directions directly in the conversation, never as YAML, JSON, a table, or a file artifact. Reply in English and use this exact hierarchical Markdown structure for each direction:

```markdown
## Direction [A/B/C]: [Direction name]

### One-line description

[One-sentence concept]

### Product integration

[How the product enters the story and frame naturally and truthfully]

### Video format

[Lifestyle Film / Integration of Animation and Lifestyle / Cinematic Animation]

### Visual tone

[Executable visual language]

### AI feasibility

[High / Medium / Low; summarize risks]
```

Embed the underlying requirements in this response: product category, narrative model, product role, brand world, core benefit, appearance strategy, product-integration naturalness (1-5), AI feasibility (1-5), technical risks, required references, and approval questions. Close with one recommendation and ask the user to select A, B, or C. Keep the entire proposal response in English.

At least one of the three directions MUST include a believable use-case setting and a person or visible human interaction. Name the setting and interaction in `Product integration`, and keep the interaction product-truthful and physically credible. The remaining directions may use a pure-product or no-person approach.

## Person Setup Rules

- **Cinematic Animation / Pure CG:** no visible person is required. In `Setup assumptions > Person`, write `No on-screen talent`; an optional hands-only interaction may appear only when it truthfully proves an approved product behavior.
- **Integration of Animation and Lifestyle: a visible person is required.** The `Setup assumptions > Person` entry must define the concise person description, appearance mode, and truthful product interaction.
- **Lifestyle Film: a visible person is required.** The `Setup assumptions > Person` entry must define the concise person description, appearance mode, and truthful product interaction.
- Use a globally legible, multi-ethnic strategy when appropriate to the approved audience and market. Never derive identity or cultural context from product-category stereotypes.
- Clothing may be minimal, tailored, streetwear, workwear, or sport-led when it supports the approved direction. Use no tank tops. Keep any non-hero accessories restrained.

Score naturalness and AI feasibility from 1-5. A score below 3 requires changing the story or production method.

## Belkin Narrative Models

Choose one primary model:

1. Stay Connected
2. Remove Friction
3. Follow the User
4. One Product, Many Moments
5. From Chaos to Control
6. Invisible Infrastructure
7. Personal Space
8. Everyday Continuity

The selected model must explain the relationship between the product world and the brand world.

## Three Belkin Video Formats

### Lifestyle Film

Keep the product inside a lifestyle world and reveal it through user behavior, camera grammar, focus, and light. End with a concentrated Hero Shot.

### Integration of Animation and Lifestyle

Use animation to show product appearance and material, then use lifestyle footage to show the use scenario.

### Cinematic Animation

Keep the product as the only protagonist in a controlled product world. Use macro-to-hero progression and feature proof.

## Treatment Handoff

The approved Treatment must export:

```yaml
treatment_schema_version: "belkin-treatment.v1"
approval_status: "DRAFT | REVIEW | APPROVED | REVISE"
creative_direction_id: ""
product_category: ""
narrative_mode: ""
narrative_model: ""
product_role: ""
brand_world: ""
appearance_strategy: ""
setup_assumptions:
  person:
    reference_basis: "persona / Consumer Insight"
    description_order: "age_range > gender > race_ethnicity > profession_or_role > clothing_style > skin_makeup_hair_direction"
    description: ""
    appearance_mode: "full_person | partial_body | silhouette | hands_only | no_on_screen_talent"
    truthful_product_interaction: ""
  location: ""
  product_state: ""
  devices_and_cables: ""
product_integration_naturalness: 0
ai_feasibility: 0
phases: []
open_approvals: []
```

Do not hand off to pre-production until `approval_status: APPROVED`.
