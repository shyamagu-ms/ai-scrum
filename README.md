# AI Scrum Template

> **🇯🇵 日本語版はこちら → [README_jp.md](README_jp.md)**

> **⚠️ Note:** This template currently operates entirely in **Japanese** (prompts, agent output, and artifacts). See [Language Notice](#️-language-notice--currently-japanese-only) for details on how to switch to English.

A project template where an AI agent team executes Scrum development.  
Leveraging GitHub Copilot's custom skills and agents, it automates a development process that follows the **Scrum Guide 2020**.

---

## Overview

This template includes **Scrum artifact templates** and **AI agent definitions** needed for Scrum development.  
As a user (stakeholder / product owner's manager), you simply write your request — the AI Scrum Team autonomously handles:

- Product Backlog creation & management
- Sprint Planning
- Daily Scrum & Development (Increment creation)
- Sprint Review & Retrospective

### AI Scrum Team

The template ships with five pre-configured AI personas (default Japanese names). These are placeholders defined in the skill files — you can rename them to fit your team.

| Agent | Role |
|---|---|
| Sato | Customer (Stakeholder Proxy) |
| Suzuki | Product Owner |
| Takahashi | Scrum Master |
| Ito | Developer |
| Tanaka | Developer |

---

## Getting Started

### Prerequisites

| Tool | Notes |
|---|---|
| **GitHub Copilot CLI** | Recommended — best experience for running skill commands |
| **VS Code + GitHub Copilot** | Also supported; requires Agent Mode to be enabled |

---

### Step 1. Write Your Request

Describe what you want to build in `scrum/order/order001.md`.

```markdown
<!-- Example: scrum/order/order001.md -->
I want a ticket management system.
I'd like status tracking and a dashboard for visualization.
```

> File numbering starts at `001`. For subsequent requests, create new files with incrementing numbers: `order002.md`, `order003.md`, etc.

---

### Step 2. Clarify the Request — `/order-create`

```
/order-create
```

The customer agent (Sato) reads the latest `orderXXX.md` and asks the user clarifying questions.  
Through this dialogue, requirements are refined and the `orderXXX.md` file is updated into a structured format the Scrum Team can act on.

---

### Step 3. Backlog Refinement — `/backlog-refinement`

```
/backlog-refinement
```

The entire AI Scrum Team participates to create and update the following based on the request:

- **Product Goal** (`product_goal.md`)
- **Product Backlog** (`product_backlog.csv`) — PBI detailing, splitting, estimation & prioritization
- **Definition of Done** (`definition_of_done.md`)

---

### Step 4. Sprint Planning — `/sprint-planning`

```
/sprint-planning
```

The AI Scrum Team conducts Sprint Planning:

1. **Why** — Why is this Sprint valuable? (Sprint Goal formulation)
2. **What** — What can be done this Sprint? (PBI selection)
3. **How** — How will the chosen work get done? (Task breakdown & assignment)

Results are recorded in a new sprint folder (`sprintXXX/`).  
Each sprint lasts **5 days** (1 week).

---

### Step 5. Daily Scrum & Development — `/one-day-in-scrum`

```
/one-day-in-scrum
```

**Each execution covers one day** of Daily Scrum and development work:

- Progress check for each developer (what was done yesterday / what's planned today / blockers)
- Sprint Backlog updates
- **Increment creation (actual code, etc.)**

> **Run this 5 times to complete the full sprint (5 days).**

---

### Step 6. Sprint Review — `/sprint-review`

```
/sprint-review
```

A review event to inspect the Increment created during the Sprint:

- Developers demo and explain the Increment
- Customer agent (Sato) provides feedback (functionality, usability, business value)
- Product Owner (Suzuki) makes accept/reject decisions for each PBI
- Product Backlog is adjusted and velocity is recorded

---

### Step 7. Sprint Retrospective — `/sprint-retrospective`

```
/sprint-retrospective
```

A retrospective event to close out the Sprint:

- **Keep** — What went well / practices to continue
- **Problem** — What went wrong / pain points
- **Try** — Improvements to experiment with in the next Sprint

Improvement actions are decided and the Definition of Done is reviewed.

---

### Next Sprint

Return to Step 1 and create `order002.md` if you have new requests, then repeat the same flow.  
If there are no changes to the request, you can resume from Step 4 (Sprint Planning).

---

## Utility Skills

These skills can be used at any time, independent of the sprint workflow.

### Ask the Product Owner — `/ask-to-po-suzuki`

```
/ask-to-po-suzuki
```

Starts an interactive dialogue session with the Product Owner (Suzuki).  
You can ask questions, request information from project files, and add or modify PBIs in the Product Backlog.

### Ad-hoc Sprint — `/adhoc-sprint`

```
/adhoc-sprint
```

Handles ad-hoc / one-off requests from the user without going through the full Scrum cycle.  
The Product Owner (Suzuki) receives the request and dispatches tasks to the appropriate sub-agents (developers, Scrum Master, reviewer), iterating with reviews from Kobayashi until the user's request is satisfied.

### User Review — `/human-review`

```
/human-review
```

Conducts a review session for the user (supervisor/stakeholder).  
The Scrum Team explains progress — per sprint or across the entire product — by showing actual web screens, and collects feedback from the user.

### Full Security Audit — `/full-security-audit`

```
/full-security-audit
```

Performs a comprehensive security assessment of the entire project.  
Runs six security reviews (source code, supply chain, configuration files, threat modeling, Scrum process, and cloud environment) in sequence, and produces a consolidated audit report under `security/reviewsXXX/`.

### Mindset — `/my-mindset`

```
/my-mindset
```

A short skill that has the agent recite its working mindset — committing to perform the instructed task faithfully and thoroughly without cutting corners or letting custom agents do the work in its place. Useful as a reminder before starting important work.

---

## Batch Execution (Experimental)

```
/execute-sprint
```

This skill runs all of Steps 1–7 in a single execution.

> **⚠️ Heads-up:** Because this is a long-running process, accuracy may degrade and the session could time out or terminate early. **Running each step individually is strongly recommended** until this mode is more stable.

---

## GitHub Agentic Workflow

This template can also be used with **GitHub Agentic Workflow (gh-aw)**.  
For details, see the official site: **<https://github.github.com/gh-aw/>**

> [!CAUTION]
> GitHub Agentic Workflow is a very new service. **You must verify behavior with the latest version before use.** Specifications and features may change without notice.

### Setup

#### 1. Install the CLI extension

If you haven't installed it yet, run:

```bash
gh extension install github/gh-aw
```

#### 2. Compile before use

Always compile before running:

```bash
gh aw compile
```

#### 3. Required tokens

The following two environment variables must be set:

| Token | Description |
|---|---|
| `GH_AW_GITHUB_TOKEN` | GitHub personal access token |
| `COPILOT_GITHUB_TOKEN` | Copilot GitHub token |

Both tokens require **Read and Write access** to:
- **Code**
- **Pull requests**
- **Workflows**

#### 4. Repository settings

The following settings must be configured on your repository:

- **Copilot Coding Agent + Agentic Workflows**: Enabled
- **Actions permissions**: Allow the following actions:
  - `github/gh-aw-actions`
  - `microsoft/apm-action`
  - `actions/*`
- **Workflow permissions**: Read and Write permissions + Allow GitHub Actions to create pull requests

---

## Rules

- All artifacts follow the **Scrum Guide 2020**
- Node.js package manager: **pnpm**
- Python projects use a virtual environment (`.venv`)
- CSV files are UTF-8 encoded; column structures must not be modified

### ⚠️ AI Model Notice

The prompts and skill definitions in this template are currently tuned for **Claude Opus 4.6** and **GPT-5.4**.  
If you are using a different AI model, you may need to adjust the prompts or skill files to suit your model's characteristics. Results may vary depending on the model used.  
Also, since this template heavily uses AI agents and consumes a large number of tokens, please check the billing model and costs for the model you are using and switch to a different model if necessary.

### ⚠️ Language Notice — Currently Japanese Only

This template's prompts, skill definitions, and all generated artifacts are currently **written in Japanese**. English speakers can still use the template, but the output will be in Japanese by default.

**To switch to English**, choose one of the following approaches:

1. **Quick fix** — Change the language rule in `.github/copilot-instructions.md` from Japanese to English. This will cause the AI agents to respond in English, though some template text may remain in Japanese.
2. **Full conversion** — Translate the entire project (Markdown files, CSV files, skill definitions, etc.) into English using GitHub Copilot or another AI-assisted tool.

> **Want a first-class English version?**  
> If there's enough demand, we plan to publish a dedicated English edition of this template. Please [open an issue](../../issues) or drop us a note — we'd love to hear from you!

---

