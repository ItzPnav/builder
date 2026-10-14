---
name: builder
description: "One entry point for every project-documentation builder: PRD, PIFS (PROJECT / FEATURES / SPEC / IMPLEMENTATION), README, plain-language project description, and AI-agent rules files (CLAUDE.md, GEMINI.md, AGENTS.md, .cursorrules, .windsurfrules). Shows a short questionnaire so the user picks which builder to run (or the full idea-to-agent-rules pipeline), then hands off to that builder's own SKILL.md. Use this whenever the user types /builder, asks to 'document my project', 'write the docs', 'which doc should I make', or requests any PRD, spec docs, README, project write-up, or agent rules/memory file, even if they don't name a specific builder."
---

# Builder

Builder is a **router**. It doesn't write documents itself. It works out which doc builder the user needs, then hands the job to that builder's own `SKILL.md`. Each builder is the expert on its own document, so it stays the single source of truth. Builder only gets the user to the right one quickly.

The builders are **sibling folders** of `builder/`. Read them; never edit them. If a builder were changed from in here, it would no longer match its standalone version or its `.skill` bundle.

| Menu # | Builder | Path (relative to this file) | Produces |
|---|---|---|---|
| 1 | Pipeline (nested) | `pipeline/SKILL.md` | All of the docs below, in order, with checkpoints |
| 2 | PRD Builder | `../prd-builder/SKILL.md` | One `[PRD] ...` product requirements doc |
| 3 | PIFS Builder | `../pifs-builder/SKILL.md` | `PROJECT.md`, `FEATURES.md`, `SPEC.md`, `IMPLEMENTATION.md` |
| 4 | README Builder | `../readme-builder/SKILL.md` | `README.md` |
| 5 | Project Describer | `../project-describer/SKILL.md` | `<project>-project-description.md` |
| 6a | Agent Rules Builder | `../agent_project_rules_builder/SKILL.md` | Any agent rules file, built from the README |
| 6b | Gemini Rules Builder (legacy) | `../gemini-builder/SKILL.md` | `GEMINI.md` only, built from the README |

For inputs, overlaps, and "which one should I pick", see `references/index.md`. Read it when the user is unsure or asks how the builders differ.

---

## Step 1: Decide whether to ask

**If the request already names one document**, e.g. "make me a PRD" or "CLAUDE.md from this README", skip the menu and go to Step 3. The user has already chosen, and asking again only adds friction.

**Otherwise** (a bare `/builder`, "document my project", "help me with docs"), show the questionnaire in Step 2 before doing anything else. Don't guess: each builder needs different inputs, so a wrong guess wastes the user's time collecting the wrong material.

## Step 2: The questionnaire

Use the interactive multiple-choice tool (`ask_question` or equivalent) to ask **one** single-select question:

> **Which project doc do you want to build?**

Options, in this order:

1. `(Recommended if starting from scratch) Full pipeline: idea → PRD → PIFS → README → project description → agent rules`
2. `PRD: product requirements doc from my idea, flowchart, and tech stack`
3. `PIFS: PROJECT / FEATURES / SPEC / IMPLEMENTATION engineering docs`
4. `README: a structured README.md for my project`
5. `Project description: explain my project to non-technical and technical readers`
6. `Agent rules file: CLAUDE.md / GEMINI.md / AGENTS.md / .cursorrules from my README`

If no interactive tool is available, show the same six options as a numbered list in chat and wait for a reply.

Keep this question about *which builder* only. Don't ask for the idea, the README, etc. here, because each builder collects its own inputs in its own way.

### Follow-up for option 6 only

Ask one more single-select question:

> **Which agent-rules builder?**

1. `(Recommended) Any agent file: I'll pick CLAUDE.md, GEMINI.md, AGENTS.md, .cursorrules, etc.` → 6a
2. `GEMINI.md only, using the original Gemini builder` → 6b

Skip this follow-up if the user already named a target file. Use 6a for any named file, including `GEMINI.md`, because 6a covers every target. Only use 6b when the user explicitly asks for the legacy or original Gemini builder.

## Step 3: Hand off

1. Open the chosen builder's `SKILL.md` from the table above and read the whole file.
2. If it says to load more files, load them from **that builder's folder**.
3. Follow it exactly as written: its input rules, its single allowed clarifying question (if it has one), its output structure, and its quality checklist. If anything here conflicts with the builder, the builder wins.
4. Don't mix rules across builders. A README follows only README Builder rules, even if the PRD Builder's style is also in context.

If a builder file is missing, tell the user which folder is expected next to `builder/` and stop. Rebuilding a builder from memory would quietly produce a different document than the user's real builder.
