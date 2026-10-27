# Builder: Builder Index

An explainer and link file. It describes the builders; it doesn't replace them.

## At a glance

| Builder | Link | Inputs | Output | Asks questions? |
|---|---|---|---|---|
| PRD | [SKILL.md](./prd-builder/SKILL.md) | Idea + flowchart + tech stack | One PRD | Once, only if one of the 3 inputs is missing |
| PIFS | [SKILL.md](./pifs-builder/SKILL.md) | Same 3 inputs (+ optional PRD.md) | PROJECT, FEATURES, SPEC, IMPLEMENTATION | Once, only if one of the 3 inputs is missing |
| README | [SKILL.md](./readme-builder/SKILL.md) | Project facts → fixed template | `README.md` | As needed to fill the template |
| Project Describer | [SKILL.md](./project-describer/SKILL.md) | Notes / abstract / spec | `<project>-project-description.md` | Yes, if source material is missing |
| Agent Rules | [SKILL.md](./agent_project_rules_builder/SKILL.md) | README.md (+ stylesheets for UI rules) | Chosen rules file | Only to pick the target file |
| Gemini Rules (legacy) | [SKILL.md](./gemini-builder/SKILL.md) | README.md (+ stylesheets for UI rules) | `GEMINI.md` | Never |
| Pipeline | [SKILL.md](../pipeline/SKILL.md) | Idea + flowchart + stack, once | All of the above | Checkpoint after each stage |

## Pick by situation

| You have... | You want... | Menu option |
|---|---|---|
| Just an idea | Every doc, start to finish | 1 Pipeline |
| Idea + rough flow + tentative stack | A product-level "why/what" doc | 2 PRD |
| Same inputs, or a finished PRD | Engineering planning docs | 3 PIFS |
| A planned or built project | A GitHub README | 4 README |
| Notes, abstract, or spec | A plain-language explainer | 5 Project description |
| A finished README | Rules for an AI coding agent | 6 Agent rules |

## Overlaps

- **6a vs 6b.** The Agent Rules Builder generalizes the Gemini builder: same extraction, plus a target-file step. Builder routes all named targets, including `GEMINI.md`, to 6a. 6b is only for an explicit request for the original Gemini builder.
- **PRD vs PIFS.** They take the same inputs in a different voice. The PRD is product-manager voice; PIFS is senior-engineer voice. PIFS treats an existing PRD as the source of truth, so build the PRD first if you want both.
- **README vs Project Describer.** The README is a strict GitHub template (badges, ASCII architecture, setup steps, no emoji). The describer is 5 prose sections for mixed readers. One doesn't replace the other.
- **The README limits the rules file.** Both rules builders read the README and any repository stylesheets, extracting full design tokens, theme cascades, micro-physics, and keyframe engines so UI rules reflect production reality.

## Notes

- `prd-builder`, `pifs-builder`, and `readme-builder` have no YAML frontmatter, so they won't auto-trigger on their own. Builder is the dependable way to reach them.
- The builders also exist as `.skill` bundles. Builder reads the extracted folders, so re-extract after you update a bundle.
- `project-docs-hub/` is an older router for the same builders. Don't install both in the same skills directory, or they'll compete for the same triggers.
