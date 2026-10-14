# GEMINI.md — builder
# Project memory for Gemini. Read this before touching ANY file.

---

## 1. PROJECT IDENTITY

- **Name:** builder
- **Type:** Antigravity Router & Pipeline Skill
- **Author handle:** ItzPnav
- **Current version:** 1.0.0
- **Purpose:** Meta-router and orchestrator providing a unified entry point and sequential pipeline for project-documentation builders (PRD, PIFS, README, Project Describer, Agent Rules).

---

## 2. FILE OWNERSHIP — WHO TOUCHES WHAT

```
SKILL.md            ← Main router skill and entry point questionnaire
pipeline/SKILL.md   ← Sequential chained execution sub-skill with stage checkpoints
references/index.md ← Explainer, builder directory, overlap guide, and decision matrix
evals/evals.json    ← Benchmark evaluation assertions and test suite
README.md           ← Project README
GEMINI.md           ← Agent project memory and behavioral rules
```

**Never create:** arbitrary scratch files outside designated directories. Never modify files inside sibling builder folders (`../prd-builder/`, `../pifs-builder/`, etc.).

---

## 5. PLATFORM/RUNTIME HARD RULES

1. **Antigravity Skill Standard** — Follow standard Antigravity skill architecture with YAML frontmatter `name` and `description`.
2. **Sibling Builder Integrity** — Sibling builders (`../prd-builder`, `../pifs-builder`, `../readme-builder`, `../project-describer`, `../agent_project_rules_builder`, `../gemini-builder`) are read-only external dependencies; never modify them.
3. **No Premature Asking** — Do not ask for document content or project specifics before determining which builder the user needs.
4. **Direct Route Bypass** — If the user names a specific target doc in their prompt, bypass the questionnaire menu directly to that builder.

---

## 8. WHAT NOT TO DO — HARD GUARDRAILS

- **Never edit sibling builders** — they are separate standalone packages and must remain identical to their `.skill` bundles.
- **Never skip user checkpoints in pipeline** — always require user confirmation between stages (PRD → PIFS → README → Describer → Rules).
- **Never guess inputs** — let each target builder prompt for its own required inputs.

---

## 10. QUICK REFERENCE — CURRENT STATE SNAPSHOT

| Thing | Value |
|---|---|
| Skill Name | builder |
| Target Type | Antigravity Skill |
| Repository | https://github.com/ItzPnav/builder.git |
| Main Entry | SKILL.md |
| Pipeline Entry | pipeline/SKILL.md |

---

## 12. CUSTOM SLASH COMMANDS

*(Fixed section — include verbatim in every generated GEMINI.md, regardless of stack.)*

### /acp — Add, Commit, Push

When the user types `/acp`:

1. Stage everything: `git add .`
2. Write a commit message summarizing the actual staged changes — **max 6–7 words, imperative mood, no trailing period** (e.g. `fix popup crash on empty state`, `add streak counter to dashboard`).
3. Commit: `git commit -m "{generated message}"`
4. Push: run `git push`. If the current branch has no upstream, run `git push -u origin main` instead.

Rules:
- Never ask the user to approve or edit the commit message — write it and proceed.
- Never skip `git add .` even if only one file changed.
- If `git commit` reports nothing to commit, say so and stop — do not push.
- If the push is rejected (e.g. diverged branch), report the exact git error; do not force-push without being explicitly told to.
