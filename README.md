# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/workflow.svg" width="28" height="28" align="center"/> **builder**

### *Unified meta-router and sequential documentation pipeline for Antigravity AI coding agent workflows*

<div align="center">
<img src="https://img.shields.io/badge/PLATFORM-ANTIGRAVITY-0F9D58?style=for-the-badge">
<img src="https://img.shields.io/badge/ORCHESTRATION-ROUTER-4285F4?style=for-the-badge">
<img src="https://img.shields.io/badge/SPEC-MARKDOWN-083FA1?style=for-the-badge">
<img src="https://img.shields.io/badge/BENCHMARK-PASSING%20100%25-F4B400?style=for-the-badge">
<img src="https://img.shields.io/badge/LICENSE-MIT-F05032?style=for-the-badge">
</div>

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/info.svg" width="22" height="22" align="center"/> **Overview**

**builder** is an intelligent meta-router and pipeline orchestrator designed to guide developers and autonomous agents seamlessly to the exact project documentation builder they need.

It uses:

* **Antigravity Router Architecture** — dynamically routes user requests to specialized sibling documentation skills without modifying external dependencies.
* **Direct Bypass Classifier** — detects explicit target requests to skip questionnaires and start building immediately.
* **Sequential Chained Pipeline** — coordinates multi-stage documentation generation from initial concept down to agent memory rules.
* **Assertion Test Suite** — verifies routing accuracy and zero-modification integrity across all builder integrations.

> Designed for developers and AI agents managing modular documentation suites in Google Antigravity.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/network.svg" width="22" height="22" align="center"/> **Architecture**

```
[USER INVOCATION: /builder OR EXPLICIT DOC INTENT]
                            │
                            ▼
┌────────────────────────────────────────────────────────┐
│                  INTENT ROUTER ENGINE                  │
│  1. Scan prompt for explicit document targets          │
│  2. Direct bypass to target builder if specified       │
│  3. Interactive 6-option selection modal if bare call   │
└────────────────────────────────────────────────────────┘
                            │
         ┌──────────────────┴──────────────────┐
         ▼                                     ▼
[DIRECT BUILDER HANDOFF]             [SEQUENTIAL PIPELINE]
• PRD Builder                        • Stage 1: PRD
• PIFS Builder                       • Stage 2: PIFS
• README Builder                     • Stage 3: README
• Project Describer                  • Stage 4: Description
• Agent Rules Builder                • Stage 5: Agent Rules
         │                                     │
         └──────────────────┬──────────────────┘
                            ▼
[GENERATED SPECIFICATION & VALIDATED ARTIFACT OUTPUTS]
```

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/sparkles.svg" width="22" height="22" align="center"/> **Features**

### <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/list-filter.svg" width="18" height="18" align="center"/> Unified Front-Door Routing
Provides a single intuitive questionnaire that classifies user documentation requirements across six distinct builder categories without asking for premature project inputs.

### <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/fast-forward.svg" width="18" height="18" align="center"/> Direct Route Bypass
Detects explicit intents like "build a PRD" or "create CLAUDE.md" in the opening prompt to bypass questionnaire modals completely and eliminate interaction friction.

### <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/milestone.svg" width="18" height="18" align="center"/> Ordered Checkpoint Pipeline
Coordinates comprehensive project documentation from idea to agent rules via an ordered sub-skill that pauses for user confirmation after every generated artifact.

### <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/shield-check.svg" width="18" height="18" align="center"/> Zero-Modification Dependency Model
Integrates with external builder skill folders as strictly read-only modules, preserving SHA256 checksums and standalone bundle compatibility.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/layers.svg" width="22" height="22" align="center"/> **Tech Stack**

| Layer | Technology |
|-------|------------|
| Orchestration | Antigravity Router Skill Architecture |
| Specification Standard | Markdown & YAML Frontmatter |
| Pipeline Execution | Nested Chained Skill Workflow |
| Verification & Quality | Assertion-Based Benchmark Suite |
| Version Control | Git & GitHub |

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/terminal.svg" width="22" height="22" align="center"/> **Setup**

1. **Clone the repository:**

```bash
git clone https://github.com/ItzPnav/builder.git
cd builder
```

2. **Verify sibling builder directories:**

```bash
ls ../prd-builder ../pifs-builder ../readme-builder ../project-describer ../agent_project_rules_builder
```

3. **Install skill in Antigravity configuration:**

```bash
cp -r . ~/.gemini/config/skills/builder
```

4. **Run the builder router:**

```bash
/builder
```

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/shield-alert.svg" width="22" height="22" align="center"/> **Production Tips**

* Treat sibling builder folders as strictly read-only dependencies to ensure standalone skill bundles remain valid.
* Avoid gathering document content before routing is complete so each specialist builder can collect its exact required schema.
* Keep references up to date with new documentation tools to maintain high router classification fidelity.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/map.svg" width="22" height="22" align="center"/> **Roadmap**

* [ ] Add automated telemetry for route selection frequency
* [ ] Support dynamic multi-document bundle generation
* [ ] Integrate automated formatting verification hooks across generated artifacts

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/lock.svg" width="22" height="22" align="center"/> **Security Notes**

* Router skills only read local template instructions and do not execute external arbitrary network requests.
* Checkpoints in the pipeline ensure human-in-the-loop review before files are written to workspace repositories.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/folder-tree.svg" width="22" height="22" align="center"/> **Folder Structure**

```
builder/
│
├── evals/
│   └── evals.json          # Benchmark test cases and assertion suites
├── pipeline/
│   └── SKILL.md            # Chained multi-document pipeline sub-skill
├── references/
│   └── index.md            # Builder directory, overlap guide, and decision matrix
├── .gitignore              # Repository file exclusion rules
├── GEMINI.md               # Agent memory and behavioral rules
├── README.md               # Project documentation
└── SKILL.md                # Main router skill and entry point questionnaire
```

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/git-pull-request.svg" width="22" height="22" align="center"/> **Contributing**

PRs and issues are welcome. Fork freely and build on top of this.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/scale.svg" width="22" height="22" align="center"/> **License**

MIT License — use freely.

---

# <img src="https://cdn.jsdelivr.net/npm/lucide-static@1.58.0/icons/heart.svg" width="22" height="22" align="center"/> **Credits**

* [Google Antigravity](https://deepmind.google/technologies/gemini/) — Agentic framework and skill runtime
* [Lucide Icons](https://lucide.dev) — Semantic vector iconography
* [Shields.io](https://shields.io) — Quality and technology status badges

---

# Made with passion by **ItzPnav**

> *One front door for all your project specifications and agent rules.*
