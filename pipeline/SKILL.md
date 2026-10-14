---
name: builder-pipeline
description: "Runs the full project-documentation pipeline in order: PRD → PIFS → README → project description → agent rules file, with a checkpoint after each stage. Each stage hands off to the matching sibling builder's SKILL.md. Use when the user picks 'Full pipeline' in /builder, or asks for 'all the docs', 'the whole doc set', or 'take my idea all the way to a CLAUDE.md'."
---

# Builder Pipeline

This sub-skill chains the doc builders so each document feeds the next. It handles only **order and handoffs**. Every stage still runs entirely under its own builder's `SKILL.md`, read in full before that stage starts.

```
Idea + Flowchart + Tech stack
        │
        ▼
 [1] PRD Builder ───────────► PRD.md
        │
        ▼
 [2] PIFS Builder ──────────► PROJECT.md, FEATURES.md, SPEC.md, IMPLEMENTATION.md
        │
        ▼
 [3] README Builder ────────► README.md
        │
        ▼
 [4] Project Describer ─────► <project>-project-description.md
        │
        ▼
 [5] Agent Rules Builder ───► CLAUDE.md / GEMINI.md / AGENTS.md / ...
```

Why this order: the PRD fixes the problem, users, and success metrics; PIFS turns that into contracts and phases; the README needs the architecture and roadmap that PIFS settles; the description draws on all of them; and the rules builder reads only the README, so the README must exist first.

## Stage table

| Stage | Builder (path relative to this file) | Ask the user for | Reuse from earlier stages |
|---|---|---|---|
| 1 | `../../prd-builder/SKILL.md` | Idea, Flowchart, Tech stack, asked **once**, here | — |
| 2 | `../../pifs-builder/SKILL.md` | Nothing new | Same three inputs + **PRD.md** as its optional PRD input |
| 3 | `../../readme-builder/SKILL.md` | Only facts no earlier doc settled (e.g. author name for the footer, repo URL) | PROJECT.md (overview, features), SPEC.md (architecture, API), IMPLEMENTATION.md (roadmap), tech stack |
| 4 | `../../project-describer/SKILL.md` | Nothing new | PROJECT.md + SPEC.md + README.md as its source material |
| 5 | `../../agent_project_rules_builder/SKILL.md` | Target file (its own Step 0) | **README.md only** |

Stage 5 deliberately ignores the PIFS docs even though they're available. That builder is designed around exactly two inputs, itself and the README. Feeding it more would produce rules that drift from what a later re-run on the README alone would give.

## Checkpoints

After each stage, show what was produced (file names plus a 2–3 line summary) and ask with the multiple-choice tool:

1. `Continue to the next stage`
2. `Revise this stage`
3. `Skip the next stage`
4. `Stop here`

This exists because each document constrains the next. Fixing a PRD mistake now is cheap; finding it after four more documents are built on it isn't.

## Starting mid-pipeline

If the user already has some of the docs (e.g. "I have a PRD and a README"), start at the first stage they don't have and treat their existing files as the outputs of the earlier stages. Don't regenerate documents they already have unless they ask.

## Consistency

The product name, tagline, CLI or binary name, and tech stack must be identical in every stage. If a later stage shows that one of them needs to change, go back and revise the earlier stage rather than letting the documents disagree.

If any builder file is missing, name the folder that's expected (a sibling of `builder/`) and stop.
