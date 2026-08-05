# Client Proposal Deck

## Purpose and Gate

Create a client-facing PPTX only after all of these are current and approved: Treatment, P2 Visual Language Board, Pre-production Package, Markdown shortlist, ImageGen storyboard-reference index, and IMAGEGEN canonical Shotlist. Use the P3 `approved_hero_asset_id` and `approved_hero_image_path`; include C01 and L01 only when P3 `reference_requirements` declares them. Do not create this deck for an external-prompt-only route.

The deck is a P6 review artifact, not a source of new creative direction. It explains the approved proposal to the stakeholder; it never adds claims, product behavior, locations, styling, images, UI, logos, CTA copy, or visual effects.

Use [WCH022 Video Treatment 2026 07 09](https://www.figma.com/design/YJ5ULXK23yVf95HIBD0mWk/WCH022---Video-Treatment---2026-07-09?node-id=0-1) as the default visual and layout reference. It is not an editable source template: never reuse its product copy, image assets, claims, or other project-specific content.

Use the workspace dependency runtime returned by `load_workspace_dependencies` for the source compiler and PPTX renderer. Do not assume plain system `python` includes PDF dependencies:

```text
<workspace-python> skills/belkin-video-orchestrator/scripts/prepare_client_proposal_deck.py <manifest> <source-package.json>
<workspace-node> skills/belkin-video-orchestrator/scripts/build_client_proposal_deck.mjs <source-package.json> 09_delivery/{PROJECT_NUMBER}-client-proposal-vNNN.pptx
```

Register the PPTX as `client-proposal-deck`, stage `DELIVERY`, with `pptx_16_9`, source versions, slide source map, `IMAGEGEN` route, and `UNAPPROVED` review status.

## Deck Structure

The client proposal deck is English, 16:9, and uses these fixed proposal pages:

1. Cover - project, product, format, duration, and proposal identity.
2. Message hierarchy - approved Treatment hierarchy.
3. Creative concept - approved Treatment concept.
4. Overall visual system - P2 colour, lighting, camera, material, and motion intent.
5. Character sheet - include only when `character` is required and C01 is approved.
6. Location sheet - include only when `location` is required and L01 is approved.
7+. Storyboard sequence - one or two approved frames per page, in stable Shot ID order, with time range, camera label, and concise description.

The deck page count is `4 + applicable reference pages + ceil(approved Shot IDs / 2)`. Each storyboard slide has one or two large 16:9 frame panels; a final odd shot receives a full-width frame. Visible descriptions are concise, client-facing summaries of the canonical Shotlist; the full approved description, frame path, asset IDs, and source versions belong in speaker notes.

## Belkin Presentation System

- Use Suisse Intl Book for body copy and Suisse Intl SemiBold for headings. Fall back to Inter only if Suisse Intl is unavailable.
- Follow the WCH022 template's 1920×1080 editorial composition: pages 2–10 use warm-paper `#F6F4EE`, compact labels, generous white space, a discreet footer, and a page number.
- Use a full-bleed Belkin Green `#6FFB38` cover with the P3-approved product hero on the right and the project title on the left. Use the approved black or white Belkin wordmark asset with guideline clear space; never typeset a substitute logo. Use Belkin Black `#000000` for hierarchy, Belkin Gray `#F4F4F4` for restrained support fields, and Belkin White `#FFFFFF` only where needed for contrast.
- Present Treatment content as large editorial copy, P2 as a concise visual-system page with restrained colour swatches, and C01/L01 as left-aligned approved descriptions with the reference image on the right when applicable. Storyboard slides retain one or two dominant 16:9 frames with concise descriptions above each frame.
- Keep the deck minimal and the storyboard frames dominant. Do not turn the deck into a dashboard, UI-card grid, moodboard, or process document.
- Embed approved C01, L01, and storyboard reference images directly in the PPTX. Never generate replacement media for the deck.
- Keep readable UI, final product geometry, logo, CTA, claims, and legal copy outside the generated storyboard image. Add one restrained footer to storyboard slides stating that they are directional and final product/design/compositing work remains approved responsibility.
- Add a `[Sources]` block to every slide's speaker notes, listing local artifact version/path and relevant frame or asset reference. Render the user-facing product format as `PDP 16:9`, not an internal identifier such as `PDP_16_9`.

## Review and Revision

After rendering and inspecting every slide, show only:

```text
a. Approve
b. Provide feedback and revise
```

For feedback, request:

```text
- Section: [slide number, slide title, Shot ID, or source phase]
  - Change: [specific revision required]
```

If feedback concerns layout, copy fit, or the deck's presentation only, record `CLIENT_PROPOSAL_DECK` feedback with no source stage, invalidate only the deck, increment its version, and remain in `PROMPT_PACKAGE_READY`.

If feedback changes approved content, record `CLIENT_PROPOSAL_DECK` feedback with one source stage: `TREATMENT`, `VISUAL_LANGUAGE`, `PREPRODUCTION`, `SHOTLIST`, or `STORYBOARD_REFERENCES`. The selected source stage reopens under its existing approval and invalidation rules. Storyboard-reference feedback must identify one or more stable Shot IDs.

On approval, record `CLIENT_PROPOSAL_DECK APPROVED`, then transition from `PROMPT_PACKAGE_READY` to `QA_REVIEW`. Do not add a new manifest state.

## QA

Before review, render every slide to PNG, inspect each page and the contact montage, and run the presentation overflow check. Resolve clipped text, unintended overlaps, stretched images, incorrect image crops, inconsistent page markers, missing source notes, or an invalid dynamic page count before presenting the deck.
