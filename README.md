# Belkin Video Assistant

## Role

Belkin Video Assistant is the user-facing planning Skill for Belkin product-video projects. It acts as the creative and production coordinator: turning an approved brief into a traceable set of Treatment, visual direction, pre-production, storyboard, shotlist, prompt, proposal-deck, and QA deliverables.

It protects approved decisions, product accuracy, brand consistency, and version history throughout the project.

## Skill Dictionary

**Treatment** — Defines the creative concept, message hierarchy, story structure, casting approach, product role, and feasibility.

**Visual Language** — Defines the approved visual system: colour, lighting, camera, materials, composition, and the relationship between CG and lifestyle worlds.

**Pre-production** — Locks product grooming, character, location, props, devices, cables, practical details, and continuity constraints.

**Shot Language** — Converts approved shot information into consistent English static-storyboard prompts, preserving product, character, location, lighting, and compositing constraints.

**Storyboard** — Turns the approved story into a connected visual shot plan, including the video spine, shot descriptions, camera language, storyboard references, and canonical shotlist.

## Scope

The Skill owns the planning workflow from intake through delivery QA. It can generate planning references—Character Sheet, Location Sheet, and storyboard frames—when the workflow explicitly allows ImageGen.

It does not invent product geometry, features, ports, UI, claims, logos, CTA, cable behaviour, or final packshots. Final product renders, motion media, compositing, logo treatment, UI, and claims remain specialist design or production responsibilities.

## Workflow

```text
P0 Intake & Context
→ P1 Creative Proposal and Treatment
→ P2 Visual Language Board
→ P3 Pre-production Package
→ P4 Unified Storyboard and Shotlist
   → ImageGen storyboard references OR external still-image prompts
   → Canonical Shotlist
→ P5 Optional Prompt Package
→ P6 Client Proposal Deck for ImageGen projects
→ QA Review and Delivery

<img width="622" height="740" alt="Screenshot 2026-08-05 171249" src="https://github.com/user-attachments/assets/0ca67f0e-1e6e-422d-9ca2-0e9b31578694" />


```

Each approved stage advances automatically. Feedback reopens only the relevant stage and invalidates only its downstream artifacts.

## Sources and Tools

The Skill works from approved project sources:

- Brief, SKU, claims, format, duration, and product reference assets
- Belkin Brand and Animation Guidelines
- Approved Treatment, Visual Language, and Pre-production artifacts
- Stable asset IDs, manifest records, and canonical Shot IDs

Its internal runtime tools manage deterministic project operations:

- `project_controller.py` — states, approvals, feedback, artifact registration, and invalidation
- `qa_project.py` — shotlist, prompt, product, and delivery QA
- `validate_project.py` — manifest validation
- `shot-language.md` — the sole compiler for English static storyboard prompts
- PDF, presentation, and ImageGen capabilities — for approved planning deliverables only

## Install in ChatGPT with Codex

This is a local Codex Skill. Use the ChatGPT desktop app with Codex; it cannot be installed into a standard browser-only ChatGPT conversation that does not support local Skills.

You do not need a GitHub account to install this public Skill. GitHub is only where the Skill files are stored. You need Internet access and a ChatGPT/Codex environment that supports Skills.

### Install it

1. Copy this repository link: [Juneouch/Belkin-Video-Assistant](https://github.com/Juneouch/Belkin-Video-Assistant).
2. Open a new task in the ChatGPT desktop app with Codex.
3. Paste the following message into the task:

   ```text
   Please install the public Codex Skill from https://github.com/Juneouch/Belkin-Video-Assistant.
   The Skill is at the repository root (SKILL.md). Install it as belkin-video-assistant.
   ```

4. Let Codex complete the download and installation. You do not need to create a GitHub account, clone the repository, or use Git commands.
5. Start a new Codex task and invoke the Skill with a request such as:

   ```text
   $belkin-video-assistant Help me plan a Belkin product video.
   ```

### If it does not appear

- Restart Codex, then start a new task. Codex normally detects newly installed Skills automatically, but a restart refreshes the available Skill list.
- If the repository link opens a `404` page, confirm that the repository has been published as public and that the link was copied exactly.
- If Codex says `belkin-video-assistant` already exists, ask it to update the existing Skill instead of manually deleting files.
- A GitHub account is only needed if you want to edit, publish, or contribute to the repository; it is not required to use this public Skill.
