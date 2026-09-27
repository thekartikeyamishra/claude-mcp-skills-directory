# Verified Claude Skills: Scored, Security-Checked Agent Skills for Claude Code (2026)

> 193 free Claude Skills (Agent Skills / `SKILL.md`), each scored out of 100 on **real pain solved, demand signal, and ideal user fit**. Works with Claude Code, Claude.ai, the Claude API, Codex, Cursor, Gemini CLI and other agents that support the Agent Skills standard.

![Skills scored](https://img.shields.io/badge/skills%20scored-193-blue?style=flat-square)
![Tier S](https://img.shields.io/badge/Tier%20S%20(%E2%89%A595)-21-brightgreen?style=flat-square)
![Last reviewed](https://img.shields.io/badge/last%20reviewed-Sep%202026-orange?style=flat-square)
![License](https://img.shields.io/badge/list%20license-CC0-lightgrey?style=flat-square)

**Why this list exists.** There are now thousands of public skills and dozens of "awesome" lists that rank them by star count. Independent testing found that most public skills add tokens and noise without improving output, that many skills silently fail to trigger, and that a meaningful share of skills on public hubs contain critical security issues. This list answers a narrower question: *which skills are worth installing, and how do you use them safely?*

> Not affiliated with or endorsed by Anthropic. "Claude" is used descriptively. Every skill links to its original source; we do not copy or redistribute skill files.

---

## Contents

- [Quick start: install and use any skill](#quick-start-install-and-use-any-skill)
- [How skills are scored](#how-skills-are-scored)
- [Tier S: the 21 skills scoring 95+](#tier-s-the-21-skills-scoring-95)
- [Full catalog by category (Tier A and B)](#full-catalog-by-category)
  - [Workflow and planning](#workflow-and-planning)
  - [Debugging, testing and verification](#debugging-testing-and-verification)
  - [Code quality and review](#code-quality-and-review)
  - [Security](#security)
  - [Frontend, UI and design](#frontend-ui-and-design)
  - [Backend, databases and APIs](#backend-databases-and-apis)
  - [Cloud, DevOps and infrastructure](#cloud-devops-and-infrastructure)
  - [Mobile: Flutter, Dart, React Native, Expo](#mobile-flutter-dart-react-native-expo)
  - [AI, ML and LLM app development](#ai-ml-and-llm-app-development)
  - [Observability](#observability)
  - [Documents and data](#documents-and-data)
  - [Research, writing and knowledge](#research-writing-and-knowledge)
  - [Growth, SEO and product for developer-founders](#growth-seo-and-product-for-developer-founders)
  - [Skill authoring and tooling](#skill-authoring-and-tooling)
- [Safety checklist before you install](#safety-checklist-before-you-install)
- [FAQ](#faq)
- [Contributing](#contributing)

---

## Quick start: install and use any skill

A skill is a folder containing a `SKILL.md` file (YAML frontmatter with `name` and `description`, then Markdown instructions), optionally with `scripts/`, `references/` and `assets/`. The agent reads only the name and description at session start and loads the full skill when your task matches.

**Method 1: skills CLI (works across most agents)**

```bash
# one skill from a repo
npx skills add <owner>/<repo> --skill <skill-name>

# every skill in a repo
npx skills add <owner>/<repo> --skill '*'
```

**Method 2: Claude Code plugin marketplace**

```bash
/plugin marketplace add anthropics/skills
/plugin install document-skills@anthropic-agent-skills
/plugin install example-skills@anthropic-agent-skills
```

**Method 3: manual copy**

```bash
# personal (all projects)
~/.claude/skills/<skill-name>/SKILL.md
# project (commit to git so your team gets it)
.claude/skills/<skill-name>/SKILL.md
```

**Using a skill.** Most skills trigger automatically when your request matches their description. You can also name it directly ("Use the pdf skill to extract the form fields from invoice.pdf") or call it as a slash command (`/skill-name`). Skills load at session start, so restart Claude Code (or run `/reload-plugins`) after installing. Run `/doctor` to check you have not exceeded the skill description budget, since overflowing skills are silently dropped.

**Install fewer, not more.** Start with 3 to 6 skills that match your daily work. Add another only when you hit a specific, repeated failure.

---

## How skills are scored

Every skill gets three sub-scores, which add up to a total out of 100.

| Parameter | Weight | What we look at |
|---|---|---|
| **P: Real pain solved** | 40 | Does it fix a failure developers repeatedly hit (skipped tests, root-cause-free bug fixes, insecure defaults, broken integrations)? Does it define "done properly" in a way the base model does not? Does it encode durable process rather than a capability the next model release will absorb? |
| **D: Demand signal** | 35 | Maintainer credibility (official vendor team or proven author), adoption (stars, installs, forks), community mentions (Reddit, X, HN, blogs), and update frequency. |
| **I: ICP fit** | 25 | Is there a clearly defined user who runs into this weekly? Is it free to use (or free with a standard account)? Is the trigger description specific enough to fire reliably? |

**Hard gates (fail any one and the skill is excluded, whatever the score):** active maintenance in the last ~90 days, a clear source repository, no obfuscated scripts or unexplained network calls, and no instruction to hide actions from the user.

**Tiers:** **S** = 95 to 100 (install-first), **A** = 85 to 94 (strong, install if it matches your stack), **B** = 75 to 84 (situational). Skills under 75 were reviewed and left out.

Scores are editorial judgments made from the signals above, as of **September 2026**. They are re-scored every quarter. A 🔑 marks skills that need a vendor account or API key; all skills themselves are free to install. Full methodology and sources: [PLAYBOOK.md](PLAYBOOK.md).

---

## Tier S: the 21 skills scoring 95+

These are the skills with the strongest evidence of real, repeated value. If you install nothing else, pick the ones that match your work from this section.

### 1. Superpowers (bundle) · 98

**What it does:** A complete development methodology packaged as composable skills: design-first brainstorming, bite-sized implementation plans, TDD enforcement, systematic debugging, git worktrees and subagent-driven execution with review. Skills trigger automatically once installed.
**Why it scores high:** Mostly encoded process rather than model capability, so it keeps its value as models improve. The most widely adopted community skill set.
**Install:**
```bash
/plugin marketplace add obra/superpowers-marketplace
/plugin install superpowers@superpowers-marketplace
```
**Use it:** Start describing a feature. Superpowers will ask clarifying questions, write a design doc, produce a plan, then execute it. Entry points: `/superpowers:brainstorm`, `/write-plan`, `/execute-plan`.
**Source:** [obra/superpowers](https://github.com/obra/superpowers) · P 39 · D 35 · I 24

### 2. systematic-debugging · 97

**What it does:** Forces a structured, four-phase root-cause process before any fix is proposed, instead of patching symptoms. Fires on any bug, failing test or unexpected behaviour.
**Install:** `npx skills add obra/superpowers --skill systematic-debugging`
**Use it:** "The checkout test fails intermittently. Debug it." The agent investigates and states the root cause before changing code.
**Source:** [obra/superpowers/skills/systematic-debugging](https://github.com/obra/superpowers/tree/main/skills/systematic-debugging) · P 39 · D 34 · I 24

### 3. verification-before-completion · 97

**What it does:** Stops the agent from declaring work "done" until it has actually run the checks that prove it (tests, builds, requirement review). Targets the most common agent failure: false completion.
**Install:** `npx skills add obra/superpowers --skill verification-before-completion`
**Use it:** Keep it installed; it activates before the agent reports completion or merges.
**Source:** [obra/superpowers/skills/verification-before-completion](https://github.com/obra/superpowers/tree/main/skills/verification-before-completion) · P 39 · D 33 · I 25

### 4. skill-creator · 97

**What it does:** Anthropic's official guide and toolkit for writing your own skills, including eval generation, benchmark mode and blind A/B comparison of "with skill" versus "without skill". Turns "I think this skill helps" into a measured result.
**Install:** `npx skills add anthropics/skills --skill skill-creator`
**Use it:** "Create a skill for how we write database migrations, with evals."
**Source:** [anthropics/skills/skill-creator](https://github.com/anthropics/skills/tree/main/skills/skill-creator) · P 38 · D 34 · I 25

### 5. test-driven-development · 96

**What it does:** Enforces RED-GREEN-REFACTOR: write a failing test, watch it fail, write the minimum code to pass, then commit. Prevents code-before-tests and untested changes.
**Install:** `npx skills add obra/superpowers --skill test-driven-development`
**Use it:** "Add rate limiting to the login endpoint." The agent writes the failing test first.
**Source:** [obra/superpowers/skills/test-driven-development](https://github.com/obra/superpowers/tree/main/skills/test-driven-development) · P 38 · D 34 · I 24

### 6. brainstorming · 96

**What it does:** Before any code, clarifies intent, success criteria and constraints through focused questions, explores alternatives, and writes a design you can correct. Stops the agent from guessing at architecture.
**Install:** `npx skills add obra/superpowers --skill brainstorming`
**Use it:** "I want to add team workspaces to my SaaS." Answer its questions, then approve the design.
**Source:** [obra/superpowers/skills/brainstorming](https://github.com/obra/superpowers/tree/main/skills/brainstorming) · P 38 · D 34 · I 24

### 7. writing-plans · 96

**What it does:** Converts an approved design into small tasks (a few minutes each) with exact file paths, code and verification steps, saved as a dated plan file.
**Install:** `npx skills add obra/superpowers --skill writing-plans`
**Use it:** After brainstorming: "Write the implementation plan."
**Source:** [obra/superpowers/skills/writing-plans](https://github.com/obra/superpowers/tree/main/skills/writing-plans) · P 38 · D 33 · I 25

### 8. webapp-testing · 96

**What it does:** Official Playwright toolkit for driving and testing your local web app: navigating, clicking, screenshots, logs. The closest official thing to an installable verification skill.
**Install:** `npx skills add anthropics/skills --skill webapp-testing`
**Use it:** "Start the dev server and verify the signup flow works end to end."
**Source:** [anthropics/skills/webapp-testing](https://github.com/anthropics/skills/tree/main/skills/webapp-testing) · P 38 · D 33 · I 25

### 9. karpathy-guidelines · 96

**What it does:** Four behavioural rules derived from Andrej Karpathy's observations on LLM coding pitfalls: think before coding, simplicity first, surgical changes, goal-driven execution. Cuts silent assumptions, over-engineering and unrelated edits.
**Install:** `npx skills add forrestchang/andrej-karpathy-skills --skill karpathy-guidelines`
**Use it:** Always-on for writing, reviewing or refactoring code. Near-zero token cost.
**Source:** [forrestchang/andrej-karpathy-skills](https://github.com/forrestchang/andrej-karpathy-skills) · P 37 · D 35 · I 24

### 10. pdf · 96

**What it does:** Extracts text, tables and form fields, fills forms, merges and splits PDFs, and creates new PDFs. Powers file handling in Claude.ai. Source-available (not open source): link to it, do not redistribute it.
**Install:** `/plugin install document-skills@anthropic-agent-skills`
**Use it:** "Extract every line item from these 12 invoices into a CSV."
**Source:** [anthropics/skills/pdf](https://github.com/anthropics/skills/tree/main/skills/pdf) · P 37 · D 35 · I 24

### 11. subagent-driven-development · 95

**What it does:** Executes a plan by sending each task to a fresh subagent with a focused prompt, reviewing each result, then reviewing the whole branch. Keeps the main context lean on long tasks.
**Install:** `npx skills add obra/superpowers --skill subagent-driven-development`
**Use it:** After writing-plans: choose "subagent-driven" execution.
**Source:** [obra/superpowers/skills/subagent-driven-development](https://github.com/obra/superpowers/tree/main/skills/subagent-driven-development) · P 37 · D 33 · I 25

### 12. docx · 95

**What it does:** Creates, edits and analyses Word documents, including tracked changes, comments and formatting. Source-available.
**Install:** `/plugin install document-skills@anthropic-agent-skills`
**Use it:** "Turn this spec into a formatted Word doc with a table of contents."
**Source:** [anthropics/skills/docx](https://github.com/anthropics/skills/tree/main/skills/docx) · P 37 · D 34 · I 24

### 13. react-best-practices (Vercel) · 95

**What it does:** Vercel Engineering's React and Next.js performance rules, grouped into eight priority levels from critical (request waterfalls, bundle size) to advanced patterns, each with wrong-versus-right examples.
**Install:** `npx skills add vercel-labs/agent-skills --skill react-best-practices`
**Use it:** "Review app/dashboard for performance issues and fix the critical ones."
**Source:** [vercel-labs/agent-skills/react-best-practices](https://github.com/vercel-labs/agent-skills/tree/main/skills/react-best-practices) · P 37 · D 34 · I 24

### 14. web-design-guidelines (Vercel) · 95

**What it does:** Audits UI code against 100+ web interface rules covering accessibility, performance and UX.
**Install:** `npx skills add vercel-labs/agent-skills --skill web-design-guidelines`
**Use it:** "Audit the settings page against the web design guidelines."
**Source:** [vercel-labs/agent-skills/web-design-guidelines](https://github.com/vercel-labs/agent-skills/tree/main/skills/web-design-guidelines) · P 37 · D 33 · I 25

### 15. mcp-builder · 95

**What it does:** Official guide to building high-quality MCP servers that connect Claude to external APIs and services, covering tool design, schemas and evaluation.
**Install:** `npx skills add anthropics/skills --skill mcp-builder`
**Use it:** "Build an MCP server for our internal orders API in TypeScript."
**Source:** [anthropics/skills/mcp-builder](https://github.com/anthropics/skills/tree/main/skills/mcp-builder) · P 37 · D 33 · I 25

### 16. static-analysis (Trail of Bits) · 95

**What it does:** Runs and interprets CodeQL, Semgrep and SARIF output to find real vulnerabilities, from a leading security firm.
**Install:** `npx skills add trailofbits/skills --skill static-analysis`
**Use it:** "Run static analysis on the payments module and triage the findings."
**Source:** [trailofbits/static-analysis](https://officialskills.sh/trailofbits/skills/static-analysis) · repo [trailofbits/skills](https://github.com/trailofbits/skills) · P 38 · D 32 · I 25

### 17. differential-review (Trail of Bits) · 95

**What it does:** Security-focused review of a diff, using git history to spot risky changes before they merge.
**Install:** `npx skills add trailofbits/skills --skill differential-review`
**Use it:** "Do a security review of this PR's diff."
**Source:** [trailofbits/differential-review](https://officialskills.sh/trailofbits/skills/differential-review) · P 38 · D 32 · I 25

### 18. grill-me (Matt Pocock) · 95

**What it does:** Interviews you relentlessly about a plan or design until every branch of the decision tree is resolved. Catches gaps before any code is written.
**Install:** `npx skills add mattpocock/skills --skill grill-me`
**Use it:** "Grill me on this migration plan."
**Source:** [mattpocock/skills/grill-me](https://github.com/mattpocock/skills/tree/main/skills/productivity/grill-me) · P 37 · D 34 · I 24

### 19. stripe-best-practices 🔑 · 95

**What it does:** Stripe's official guidance for building payment integrations correctly, where mistakes cost real money (webhooks, idempotency, API usage).
**Install:** see source page.
**Use it:** "Add Stripe subscriptions with proper webhook handling."
**Source:** [stripe/stripe-best-practices](https://officialskills.sh/stripe/skills/stripe-best-practices) · P 38 · D 32 · I 25

### 20. postgres-best-practices (Supabase) · 95

**What it does:** Supabase's PostgreSQL best practices for schema design, queries, indexing and security.
**Install:** `npx skills add supabase/agent-skills`
**Use it:** "Review this schema and the slow queries in /db for problems."
**Source:** [supabase/postgres-best-practices](https://officialskills.sh/supabase/skills/postgres-best-practices) · P 37 · D 33 · I 25

### 21. frontend-design · 95

**What it does:** Official guidance for distinctive, intentional UI instead of generic "AI-looking" layouts: typography, colour, layout and aesthetic direction.
**Install:** `npx skills add anthropics/skills --skill frontend-design`
**Use it:** "Build a landing page for a developer tool; avoid the generic look."
**Source:** [anthropics/skills/frontend-design](https://github.com/anthropics/skills/tree/main/skills/frontend-design) · P 36 · D 35 · I 24

---

## Full catalog by category

Columns: **P** pain /40 · **D** demand /35 · **I** ICP fit /25 · **Score** /100. Tier S skills are listed above and not repeated.

### Workflow and planning

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [handoff](https://github.com/mattpocock/skills/tree/main/skills/productivity/handoff) | Compacts the current session into a handoff document so a fresh session or another agent continues the work. Use before hitting context limits. | `npx skills add mattpocock/skills --skill handoff` | 36 | 33 | 25 | **94** |
| [executing-plans](https://github.com/obra/superpowers/tree/main/skills/executing-plans) | Implements a written plan inline in the current session, with one full-branch review at the end. The cheaper alternative to subagent execution. | `npx skills add obra/superpowers --skill executing-plans` | 36 | 33 | 24 | **93** |
| [using-git-worktrees](https://github.com/obra/superpowers/tree/main/skills/using-git-worktrees) | Creates an isolated worktree on a new branch, runs setup and confirms a clean test baseline before feature work. | `npx skills add obra/superpowers --skill using-git-worktrees` | 35 | 33 | 24 | **92** |
| [finishing-a-development-branch](https://github.com/obra/superpowers/tree/main/skills/finishing-a-development-branch) | Guides wrapping up a branch: verify, then choose merge, PR or cleanup. | `npx skills add obra/superpowers --skill finishing-a-development-branch` | 34 | 33 | 24 | **91** |
| [dispatching-parallel-agents](https://github.com/obra/superpowers/tree/main/skills/dispatching-parallel-agents) | Splits independent problems across parallel subagents. Use for multiple unrelated failures. Overlaps with subagent-driven-development. | `npx skills add obra/superpowers --skill dispatching-parallel-agents` | 33 | 32 | 23 | **88** |
| [grill-with-docs](https://github.com/mattpocock/skills/tree/main/skills/engineering/grill-with-docs) | Grill-me plus a shared domain vocabulary: updates CONTEXT.md and ADRs as decisions are made. | `npx skills add mattpocock/skills --skill grill-with-docs` | 34 | 31 | 23 | **88** |
| [improve-codebase-architecture](https://github.com/mattpocock/skills) | Scans the codebase for architectural friction, presents an HTML report, then walks through a chosen fix. | `npx skills add mattpocock/skills --skill improve-codebase-architecture` | 34 | 31 | 22 | **87** |
| [blueprint (imbue)](https://github.com/imbue-ai/blueprint) | Planning copilot: explores the codebase, asks clarifying questions, writes a Markdown plan any agent can execute. | see repo | 32 | 27 | 22 | **81** |
| [plannotator](https://github.com/backnotprop/plannotator) | Visual plan-review UI for Claude Code: annotate a plan before execution. | see repo | 31 | 27 | 22 | **80** |
| [crit](https://github.com/tomasz-tomczyk/crit) | Comment on plans, diffs and frontend output, then send the feedback straight to the agent. | see repo | 30 | 25 | 22 | **77** |
| [kanban-skill](https://github.com/mattjoyce/kanban-skill) | File-based Markdown Kanban with YAML status, priority and dependencies; no database. | see repo | 29 | 24 | 22 | **75** |

### Debugging, testing and verification

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [playwright-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/playwright-skill) | Generates Playwright E2E tests in TS, JS, Python, Java or C#. | `npx skills add LambdaTest/agent-skills --skill playwright-skill` | 35 | 30 | 24 | **89** |
| [pytest-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/pytest-skill) | Generates pytest suites with fixtures, parametrize and mocking. | `npx skills add LambdaTest/agent-skills --skill pytest-skill` | 34 | 29 | 24 | **87** |
| [vitest-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/vitest-skill) | Generates Vitest tests with the Jest-compatible API and ESM support. | `npx skills add LambdaTest/agent-skills --skill vitest-skill` | 34 | 29 | 24 | **87** |
| [jest-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/jest-skill) | Generates Jest unit and integration tests with mocking and snapshots. | `npx skills add LambdaTest/agent-skills --skill jest-skill` | 33 | 29 | 24 | **86** |
| [property-based-testing (Trail of Bits)](https://officialskills.sh/trailofbits/skills/property-based-testing) | Property-based tests across languages to catch edge cases example tests miss. | `npx skills add trailofbits/skills --skill property-based-testing` | 34 | 29 | 23 | **86** |
| [debug-skill](https://github.com/AlmogBaku/debug-skill) | Gives the agent a real debugger: breakpoints, stepping, variable inspection and stack traces via CLI. | see repo | 34 | 26 | 23 | **83** |
| [cicd-pipeline-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/cicd-pipeline-skill) | Generates test CI pipelines for GitHub Actions, Jenkins, GitLab CI and Azure DevOps. | `npx skills add LambdaTest/agent-skills --skill cicd-pipeline-skill` | 32 | 28 | 23 | **83** |
| [cypress-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/cypress-skill) | Generates Cypress E2E and component tests in JS or TS. | `npx skills add LambdaTest/agent-skills --skill cypress-skill` | 32 | 28 | 23 | **83** |
| [test-framework-migration-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/test-framework-migration-skill) | Migrates suites between Selenium, Playwright, Puppeteer and Cypress. | `npx skills add LambdaTest/agent-skills --skill test-framework-migration-skill` | 33 | 26 | 22 | **81** |
| [test-fixing](https://github.com/mhattingpete/claude-skills-marketplace/tree/main/engineering-workflow-plugin/skills/test-fixing) | Finds failing tests and proposes targeted fixes. | see repo | 31 | 25 | 22 | **78** |
| [pypict-claude-skill](https://github.com/omkamal/pypict-claude-skill) | Designs pairwise (PICT) combinatorial test cases to maximise coverage with few tests. | see repo | 30 | 24 | 21 | **75** |

### Code quality and review

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [requesting-code-review](https://github.com/obra/superpowers/tree/main/skills/requesting-code-review) | Structures a review request after major work so a reviewer (human or subagent) checks it against requirements. | `npx skills add obra/superpowers --skill requesting-code-review` | 35 | 33 | 24 | **92** |
| [receiving-code-review](https://github.com/obra/superpowers/tree/main/skills/receiving-code-review) | Makes the agent verify review feedback technically before applying it, instead of agreeing blindly. | `npx skills add obra/superpowers --skill receiving-code-review` | 35 | 32 | 24 | **91** |
| [composition-patterns (Vercel)](https://github.com/vercel-labs/agent-skills/tree/main/skills/composition-patterns) | React patterns that avoid boolean-prop sprawl: compound components, lifted state, composed internals. | `npx skills add vercel-labs/agent-skills --skill composition-patterns` | 33 | 32 | 24 | **89** |
| [modern-python (Trail of Bits)](https://officialskills.sh/trailofbits/skills/modern-python) | Modern Python tooling: uv, ruff, ty and pytest conventions. | `npx skills add trailofbits/skills --skill modern-python` | 32 | 30 | 24 | **86** |
| [ask-questions-if-underspecified (Trail of Bits)](https://officialskills.sh/trailofbits/skills/ask-questions-if-underspecified) | Makes the agent ask for clarification on ambiguous requirements instead of guessing. | `npx skills add trailofbits/skills --skill ask-questions-if-underspecified` | 33 | 29 | 23 | **85** |
| [caveman](https://github.com/mattpocock/skills/tree/main/skills/productivity/caveman) | Terse output mode that sharply reduces output tokens. Use when token spend is a real constraint. | `npx skills add mattpocock/skills --skill caveman` | 31 | 31 | 22 | **84** |
| [go-agent-skills](https://github.com/eduardo-sl/go-agent-skills) | 28 Go skills: code review, concurrency safety, testing, gRPC and architecture. | see repo | 31 | 25 | 23 | **79** |
| [claude-skills (jeffallan)](https://github.com/jeffallan/claude-skills) | 65 full-stack skills covering React, NestJS, Python, DevOps and 30+ frameworks. Install selectively. | see repo | 29 | 27 | 21 | **77** |
| [agent-lsp](https://github.com/blackwell-systems/agent-lsp) | Semantic code intelligence: rename, refactor and impact analysis via language servers. | see repo | 31 | 23 | 22 | **76** |

### Security

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [insecure-defaults (Trail of Bits)](https://officialskills.sh/trailofbits/skills/insecure-defaults) | Finds hardcoded secrets, default credentials and weak crypto configurations. | `npx skills add trailofbits/skills --skill insecure-defaults` | 38 | 31 | 25 | **94** |
| [variant-analysis (Trail of Bits)](https://officialskills.sh/trailofbits/skills/variant-analysis) | After one bug is found, hunts for similar vulnerabilities elsewhere by pattern. | `npx skills add trailofbits/skills --skill variant-analysis` | 36 | 30 | 24 | **90** |
| [sharp-edges (Trail of Bits)](https://officialskills.sh/trailofbits/skills/sharp-edges) | Flags error-prone APIs and dangerous configurations in your code. | `npx skills add trailofbits/skills --skill sharp-edges` | 35 | 30 | 24 | **89** |
| [security-threat-model (OpenAI)](https://officialskills.sh/openai/skills/security-threat-model) | Builds a repo-specific threat model identifying trust boundaries. | see source page | 35 | 29 | 24 | **88** |
| [semgrep-rule-creator (Trail of Bits)](https://officialskills.sh/trailofbits/skills/semgrep-rule-creator) | Writes and refines custom Semgrep rules for your codebase's bug classes. | `npx skills add trailofbits/skills --skill semgrep-rule-creator` | 34 | 29 | 23 | **86** |
| [owasp-security](https://github.com/agamm/claude-code-owasp) | OWASP Top 10:2025, ASVS 5.0 and agentic-AI security checklists with language-specific pitfalls for 20+ languages. | see repo | 35 | 27 | 24 | **86** |
| [VibeSec-Skill](https://github.com/BehiSecc/VibeSec-Skill) | Steers the agent to write secure web app code and avoid common vulnerabilities while building. | see repo | 35 | 27 | 24 | **86** |
| [security-best-practices (OpenAI)](https://officialskills.sh/openai/skills/security-best-practices) | Reviews code for language-specific security vulnerabilities. | see source page | 34 | 28 | 23 | **85** |
| [varlock-claude-skill](https://github.com/wrsmith108/varlock-claude-skill) | Keeps secrets out of Claude sessions, terminals, logs and commits. | see repo | 35 | 25 | 24 | **84** |
| [audit-context-building (Trail of Bits)](https://officialskills.sh/trailofbits/skills/audit-context-building) | Builds deep architectural context through granular code analysis before an audit. | `npx skills add trailofbits/skills --skill audit-context-building` | 33 | 28 | 22 | **83** |
| [testing-handbook-skills (Trail of Bits)](https://officialskills.sh/trailofbits/skills/testing-handbook-skills) | Fuzzers, sanitizers and static analysis from the Trail of Bits Testing Handbook. | `npx skills add trailofbits/skills --skill testing-handbook-skills` | 32 | 28 | 22 | **82** |
| [firebase-apk-scanner (Trail of Bits)](https://officialskills.sh/trailofbits/skills/firebase-apk-scanner) | Scans Android APKs for Firebase misconfigurations and security flaws. | `npx skills add trailofbits/skills --skill firebase-apk-scanner` | 34 | 26 | 22 | **82** |
| [building-secure-contracts (Trail of Bits)](https://officialskills.sh/trailofbits/skills/building-secure-contracts) | Smart contract security toolkit with scanners for six blockchains. | `npx skills add trailofbits/skills --skill building-secure-contracts` | 33 | 27 | 20 | **80** |
| [ffuf_claude_skill](https://github.com/jthack/ffuf_claude_skill) | Runs the ffuf web fuzzer and analyses the results for vulnerabilities. Only test systems you are authorised to test. | see repo | 30 | 25 | 20 | **75** |

### Frontend, UI and design

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [next-best-practices (Vercel)](https://officialskills.sh/vercel-labs/skills/next-best-practices) | Next.js recommended patterns from the Vercel team. | see source page | 35 | 32 | 25 | **92** |
| [web-artifacts-builder](https://github.com/anthropics/skills/tree/main/skills/web-artifacts-builder) | Builds complex multi-component claude.ai artifacts with React, Tailwind and shadcn/ui. | `npx skills add anthropics/skills --skill web-artifacts-builder` | 33 | 33 | 23 | **89** |
| [next-upgrade (Vercel)](https://officialskills.sh/vercel-labs/skills/next-upgrade) | Upgrades Next.js projects to newer versions, handling breaking changes. | see source page | 35 | 30 | 23 | **88** |
| [next-cache-components (Vercel)](https://officialskills.sh/vercel-labs/skills/next-cache-components) | Caching strategies and cache-aware components in Next.js. | see source page | 33 | 30 | 23 | **86** |
| [figma-implement-design](https://officialskills.sh/figma/skills/figma-implement-design) 🔑 | Translates Figma designs into production code with close visual fidelity via the Figma MCP server. | see source page | 33 | 30 | 23 | **86** |
| [react-view-transitions (Vercel)](https://github.com/vercel-labs/agent-skills/tree/main/skills/react-view-transitions) | Native-feeling animations with React's View Transition API, including Next.js integration. | `npx skills add vercel-labs/agent-skills --skill react-view-transitions` | 30 | 30 | 23 | **83** |
| [theme-factory](https://github.com/anthropics/skills/tree/main/skills/theme-factory) | Applies professional themes to artifacts or generates a custom theme. | `npx skills add anthropics/skills --skill theme-factory` | 29 | 31 | 22 | **82** |
| [figma-generate-library](https://officialskills.sh/figma/skills/figma-generate-library) 🔑 | Builds or updates a Figma design-system library from your codebase. | see source page | 31 | 28 | 22 | **81** |
| [Superdesign](https://github.com/superdesigndev/superdesign-skill) | Derives a design system from your codebase and iterates UI drafts on a canvas. | see repo | 30 | 26 | 22 | **78** |
| [canvas-design](https://github.com/anthropics/skills/tree/main/skills/canvas-design) | Produces visual designs (posters, graphics) as PNG and PDF. | `npx skills add anthropics/skills --skill canvas-design` | 26 | 31 | 20 | **77** |
| [email-html-mjml](https://github.com/framix-team/skill-email-html-mjml) | Generates responsive, cross-client HTML email using MJML with validation. | see repo | 30 | 23 | 22 | **75** |

### Backend, databases and APIs

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [upgrade-stripe](https://officialskills.sh/stripe/skills/upgrade-stripe) 🔑 | Upgrades Stripe SDK and API versions safely. | see source page | 35 | 30 | 24 | **89** |
| [better-auth best-practices](https://officialskills.sh/better-auth/skills/best-practices) | Correct Better Auth integration patterns. | see source page | 34 | 29 | 24 | **87** |
| [neon-postgres](https://officialskills.sh/neondatabase/skills/neon-postgres) 🔑 | Best practices for Neon serverless Postgres. | see source page | 33 | 29 | 24 | **86** |
| [graphql-schema (Apollo)](https://officialskills.sh/apollographql/skills/graphql-schema) | Designing clean, evolvable GraphQL schemas. | see source page | 33 | 29 | 23 | **85** |
| [auth0-quickstart](https://officialskills.sh/auth0/skills/auth0-quickstart) 🔑 | Detects your framework and scaffolds Auth0 integration. | see source page | 33 | 28 | 23 | **84** |
| [auth0-nextjs](https://officialskills.sh/auth0/skills/auth0-nextjs) 🔑 | Adds Auth0 authentication to Next.js apps. | see source page | 32 | 28 | 23 | **83** |
| [clickhouse-best-practices](https://officialskills.sh/clickhouse/skills/clickhouse-best-practices) | Best practices for ClickHouse schemas and queries. | see source page | 32 | 28 | 22 | **82** |
| [apollo-client](https://officialskills.sh/apollographql/skills/apollo-client) | Building React apps with Apollo Client 4. | see source page | 31 | 28 | 22 | **81** |
| [apollo-server](https://officialskills.sh/apollographql/skills/apollo-server) | Building GraphQL servers with Apollo Server 5. | see source page | 31 | 28 | 22 | **81** |
| [fastapi-router-py (Microsoft)](https://officialskills.sh/microsoft/skills/fastapi-router-py) | FastAPI routers with CRUD and auth patterns. | see source page | 31 | 27 | 23 | **81** |
| [pydantic-models-py (Microsoft)](https://officialskills.sh/microsoft/skills/pydantic-models-py) | Pydantic models for API schemas. | see source page | 30 | 27 | 23 | **80** |
| [postgres (read-only)](https://github.com/sanjay3290/ai-skills/tree/main/skills/postgres) | Safe read-only SQL against PostgreSQL with multi-connection support and defence-in-depth. | see repo | 32 | 24 | 23 | **79** |
| [wp-plugin-development (WordPress)](https://officialskills.sh/WordPress/skills/wp-plugin-development) | WordPress plugin architecture, hooks, settings API and security. | see source page | 31 | 27 | 21 | **79** |
| [wp-block-development (WordPress)](https://officialskills.sh/WordPress/skills/wp-block-development) | Gutenberg blocks: block.json, attributes, rendering and deprecations. | see source page | 30 | 27 | 21 | **78** |
| [wp-performance (WordPress)](https://officialskills.sh/WordPress/skills/wp-performance) | WordPress profiling, caching and database optimisation. | see source page | 30 | 26 | 21 | **77** |
| [qdrant-skills](https://github.com/qdrant/skills) | Vector search operations, performance, deployment and SDK usage for Qdrant. | see repo | 29 | 26 | 21 | **76** |
| [mailtrap-skills](https://github.com/mailtrap/mailtrap-skills) 🔑 | Email sending, sandbox testing and domain setup via Mailtrap. | see repo | 29 | 24 | 22 | **75** |

### Cloud, DevOps and infrastructure

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [workers-best-practices (Cloudflare)](https://officialskills.sh/cloudflare/skills/workers-best-practices) | Reviews and writes Workers code against production best practices and wrangler.jsonc conventions. | `npx skills add cloudflare/skills --skill workers-best-practices` | 35 | 31 | 24 | **90** |
| [gh-fix-ci (OpenAI)](https://officialskills.sh/openai/skills/gh-fix-ci) | Debugs and fixes failing GitHub Actions checks by reading the logs. | see source page | 36 | 29 | 24 | **89** |
| [cloudflare (platform)](https://officialskills.sh/cloudflare/skills/cloudflare) | Broad Cloudflare skill: Workers, Pages, storage, AI, networking, security and IaC. | `npx skills add cloudflare/skills --skill cloudflare` | 33 | 31 | 24 | **88** |
| [wrangler (Cloudflare)](https://officialskills.sh/cloudflare/skills/wrangler) | Deploys and manages Workers, KV, R2, D1, Queues and Workflows. | `npx skills add cloudflare/skills --skill wrangler` | 33 | 30 | 24 | **87** |
| [terraform-style-guide (HashiCorp)](https://officialskills.sh/hashicorp/skills/terraform-style-guide) | Writes Terraform HCL following HashiCorp's official style conventions. | `npx skills add hashicorp/agent-skills --skill terraform-style-guide` | 33 | 30 | 23 | **86** |
| [terraform-test (HashiCorp)](https://officialskills.sh/hashicorp/skills/terraform-test) | Uses Terraform's built-in testing framework with .tftest.hcl files. | `npx skills add hashicorp/agent-skills --skill terraform-test` | 33 | 29 | 23 | **85** |
| [vercel-optimize](https://github.com/vercel-labs/agent-skills/tree/main/skills/vercel-optimize) 🔑 | Audits a Vercel project for cost, performance, caching and function usage, starting from real metrics. | `npx skills add vercel-labs/agent-skills --skill vercel-optimize` | 34 | 28 | 22 | **84** |
| [web-perf (Cloudflare)](https://officialskills.sh/cloudflare/skills/web-perf) | Audits Core Web Vitals and render-blocking resources. | `npx skills add cloudflare/skills --skill web-perf` | 32 | 29 | 23 | **84** |
| [refactor-module (HashiCorp)](https://officialskills.sh/hashicorp/skills/refactor-module) | Turns monolithic Terraform into reusable modules. | `npx skills add hashicorp/agent-skills --skill refactor-module` | 32 | 29 | 22 | **83** |
| [terraform-search-import (HashiCorp)](https://officialskills.sh/hashicorp/skills/terraform-search-import) | Discovers existing cloud resources and bulk-imports them into Terraform state. | `npx skills add hashicorp/agent-skills --skill terraform-search-import` | 33 | 28 | 22 | **83** |
| [durable-objects (Cloudflare)](https://officialskills.sh/cloudflare/skills/durable-objects) | Stateful coordination with RPC, SQLite and WebSockets. | `npx skills add cloudflare/skills --skill durable-objects` | 31 | 29 | 22 | **82** |
| [deploy-to-vercel](https://github.com/vercel-labs/agent-skills/tree/main/skills/deploy-to-vercel) | Deploys an app to Vercel from the conversation, auto-detecting the framework. | `npx skills add vercel-labs/agent-skills --skill deploy-to-vercel` | 29 | 30 | 23 | **82** |
| [netlify-functions](https://officialskills.sh/netlify/skills/netlify-functions) | Serverless API endpoints and background tasks on Netlify. | see source page | 30 | 28 | 22 | **80** |
| [netlify-cli-and-deploy](https://officialskills.sh/netlify/skills/netlify-cli-and-deploy) | Netlify CLI setup, local dev and deployment workflows. | see source page | 29 | 28 | 22 | **79** |
| [aws-skills](https://github.com/zxkane/aws-skills) | AWS CDK best practices, cost optimisation and serverless patterns. | see repo | 31 | 25 | 22 | **78** |
| [cloud-solution-architect (Microsoft)](https://officialskills.sh/microsoft/skills/cloud-solution-architect) | Designs well-architected Azure systems. | see source page | 29 | 27 | 21 | **77** |

### Mobile: Flutter, Dart, React Native, Expo

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [flutter/skills (official)](https://github.com/flutter/skills) | Official Flutter skills: responsive layouts, declarative routing, JSON serialisation. Pairs with the Dart and Flutter MCP server. | `npx skills add flutter/skills --skill '*' --agent universal` | 35 | 32 | 25 | **92** |
| [dart-lang/skills (official)](https://github.com/dart-lang/skills) | Official Dart skills: unit tests, dependency resolution, static analysis fixes. | `npx skills add dart-lang/skills --skill '*' --agent universal` | 34 | 31 | 25 | **90** |
| [react-native-best-practices (Callstack)](https://officialskills.sh/callstackincubator/skills/react-native-best-practices) | React Native performance optimisation from Callstack. | see source page | 34 | 30 | 24 | **88** |
| [firebase agent skills (official)](https://github.com/firebase/agent-skills) | Official Firebase skills for Auth, Firestore, Functions and Hosting workflows. | `npx skills add firebase/skills` | 34 | 29 | 24 | **87** |
| [react-native-skills (Vercel)](https://github.com/vercel-labs/agent-skills/tree/main/skills/react-native-skills) | React Native and Expo best practices: lists, animations, navigation and monorepos. | `npx skills add vercel-labs/agent-skills --skill react-native-skills` | 33 | 30 | 24 | **87** |
| [upgrading-expo](https://officialskills.sh/expo/skills/upgrading-expo) | Upgrades Expo SDK versions. | see source page | 34 | 29 | 23 | **86** |
| [building-native-ui (Expo)](https://officialskills.sh/expo/skills/building-native-ui) | Expo Router, styling, components, navigation and animations. | see source page | 32 | 29 | 23 | **84** |
| [upgrading-react-native (Callstack)](https://officialskills.sh/callstackincubator/skills/upgrading-react-native) | React Native upgrade workflow: templates, dependencies and common pitfalls. | see source page | 33 | 28 | 23 | **84** |
| [expo-deployment](https://officialskills.sh/expo/skills/expo-deployment) | Deploys Expo apps to production. | see source page | 31 | 28 | 23 | **82** |
| [flutter-testing-skill (TestMu)](https://github.com/LambdaTest/agent-skills/tree/main/flutter-testing-skill) | Generates Flutter widget, integration and golden tests in Dart. | `npx skills add LambdaTest/agent-skills --skill flutter-testing-skill` | 32 | 26 | 23 | **81** |
| [native-data-fetching (Expo)](https://officialskills.sh/expo/skills/native-data-fetching) | Network requests, caching and offline support in Expo. | see source page | 30 | 27 | 22 | **79** |

### AI, ML and LLM app development

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [claude-api](https://github.com/anthropics/skills/tree/main/skills/claude-api) | Official guidance for building with the Claude API and SDKs. | `npx skills add anthropics/skills --skill claude-api` | 34 | 32 | 24 | **90** |
| [gemini-api-dev (Google)](https://officialskills.sh/google-gemini/skills/gemini-api-dev) 🔑 | Best practices for Gemini API apps. | see source page | 33 | 30 | 23 | **86** |
| [hugging-face-model-trainer](https://officialskills.sh/huggingface/skills/hugging-face-model-trainer) 🔑 | Trains models with TRL (SFT, DPO, GRPO) and converts to GGUF. | see source page | 33 | 29 | 22 | **84** |
| [hf-cli (Hugging Face)](https://officialskills.sh/huggingface/skills/hf-cli) | Hugging Face Hub operations via the HF CLI. | see source page | 31 | 29 | 23 | **83** |
| [firecrawl-build](https://officialskills.sh/firecrawl/skills/firecrawl-build) 🔑 | Integrates Firecrawl search, scraping and extraction into app code. | see source page | 31 | 29 | 22 | **82** |
| [gemini-live-api-dev (Google)](https://officialskills.sh/google-gemini/skills/gemini-live-api-dev) 🔑 | Real-time bidirectional streaming apps with the Gemini Live API. | see source page | 31 | 28 | 22 | **81** |
| [huggingface-gradio](https://officialskills.sh/huggingface/skills/huggingface-gradio) | Builds Gradio apps and deploys them to HF Spaces. | see source page | 30 | 28 | 22 | **80** |
| [transformers.js (Hugging Face)](https://officialskills.sh/huggingface/skills/transformers.js) | Runs ML models in the browser with Transformers.js. | see source page | 30 | 28 | 22 | **80** |
| [hugging-face-datasets](https://officialskills.sh/huggingface/skills/hugging-face-datasets) | Creates and manages datasets with configs and SQL querying. | see source page | 29 | 28 | 22 | **79** |
| [jupyter-notebook (OpenAI)](https://officialskills.sh/openai/skills/jupyter-notebook) | Clean, reproducible Jupyter notebooks for experiments and tutorials. | see source page | 29 | 27 | 22 | **78** |
| [claude-scientific-skills](https://github.com/K-Dense-AI/claude-scientific-skills) | 125+ skills for bioinformatics, cheminformatics, clinical research and ML. Install selectively. | see repo | 30 | 27 | 20 | **77** |
| [remotion](https://officialskills.sh/remotion-dev/skills/remotion) | Programmatic video creation with React. | see source page | 28 | 28 | 20 | **76** |

### Observability

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [sentry-fix-issues](https://officialskills.sh/getsentry/skills/sentry-fix-issues) 🔑 | Finds and fixes production issues using Sentry stack traces, breadcrumbs and traces via MCP. | see source page | 36 | 30 | 24 | **90** |
| [sentry-sdk-setup](https://officialskills.sh/getsentry/skills/sentry-sdk-setup) 🔑 | Detects your platform and sets up the right Sentry SDK. | see source page | 33 | 30 | 24 | **87** |
| [sentry-code-review](https://officialskills.sh/getsentry/skills/sentry-code-review) 🔑 | Reviews changes using Sentry issue and trace context. | see source page | 33 | 28 | 23 | **84** |
| [sentry-setup-ai-monitoring](https://officialskills.sh/getsentry/skills/sentry-setup-ai-monitoring) 🔑 | Instruments OpenAI, Anthropic, Vercel AI, LangChain and other LLM SDKs for monitoring. | see source page | 32 | 28 | 23 | **83** |
| [sentry-nextjs-sdk](https://officialskills.sh/getsentry/skills/sentry-nextjs-sdk) 🔑 | Full Sentry setup for Next.js App and Pages Router. | see source page | 31 | 28 | 23 | **82** |
| [sentry-python-sdk](https://officialskills.sh/getsentry/skills/sentry-python-sdk) 🔑 | Full Sentry setup for Django, Flask, FastAPI, Celery and more. | see source page | 31 | 28 | 23 | **82** |
| [sentry-flutter-sdk](https://officialskills.sh/getsentry/skills/sentry-flutter-sdk) 🔑 | Full Sentry setup for Flutter and Dart on all platforms. | see source page | 31 | 27 | 23 | **81** |

### Documents and data

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [pptx](https://github.com/anthropics/skills/tree/main/skills/pptx) | Reads, creates and edits PowerPoint decks with layouts and templates. Source-available. | `/plugin install document-skills@anthropic-agent-skills` | 34 | 34 | 25 | **93** |
| [xlsx](https://github.com/anthropics/skills/tree/main/skills/xlsx) | Spreadsheets with formulas, charts and transformations. Testers report smaller gains than docx or pdf. Source-available. | `/plugin install document-skills@anthropic-agent-skills` | 31 | 34 | 25 | **90** |
| [doc-coauthoring](https://github.com/anthropics/skills/tree/main/skills/doc-coauthoring) | Structured workflow for co-writing specs, proposals and docs with you. | `npx skills add anthropics/skills --skill doc-coauthoring` | 31 | 31 | 23 | **85** |
| [csv-data-summarizer](https://github.com/coffeefuelbump/csv-data-summarizer-claude-skill) | Profiles a CSV: columns, distributions, missing data and correlations. | see repo | 31 | 26 | 23 | **80** |
| [internal-comms](https://github.com/anthropics/skills/tree/main/skills/internal-comms) | Status reports, leadership updates, incident reports and newsletters. | `npx skills add anthropics/skills --skill internal-comms` | 27 | 31 | 21 | **79** |

### Research, writing and knowledge

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [writing-guidelines (Vercel)](https://github.com/vercel-labs/agent-skills/tree/main/skills/writing-guidelines) | Audits docs and prose against 80+ rules from the Vercel writing handbook. Great for READMEs and docs. | `npx skills add vercel-labs/agent-skills --skill writing-guidelines` | 31 | 30 | 23 | **84** |
| [avoid-ai-writing](https://github.com/conorbronsdon/avoid-ai-writing) | Detects and rewrites common AI-writing patterns in two passes. | see repo | 31 | 27 | 23 | **81** |
| [paper-search](https://github.com/ykdojo/paper-search) | Searches 250M+ academic works via OpenAlex; free, no API key. | see repo | 29 | 26 | 22 | **77** |
| [article-extractor](https://github.com/michalparkola/tapestry-skills-for-claude-code/tree/main/article-extractor) | Pulls clean article text and metadata from web pages. | see repo | 28 | 25 | 22 | **75** |
| [youtube-transcript](https://github.com/michalparkola/tapestry-skills-for-claude-code/tree/main/youtube-transcript) | Fetches YouTube transcripts and prepares summaries. | see repo | 28 | 25 | 22 | **75** |

### Growth, SEO and product for developer-founders

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [seo-audit](https://github.com/coreyhaines31/marketingskills/tree/main/skills/seo-audit) | Diagnoses technical and on-page SEO issues on a site. | `npx skills add coreyhaines31/marketingskills --skill seo-audit` | 32 | 29 | 24 | **85** |
| [schema-markup](https://github.com/coreyhaines31/marketingskills/tree/main/skills/schema-markup) | Adds and fixes structured data for rich results. | `npx skills add coreyhaines31/marketingskills --skill schema-markup` | 31 | 28 | 24 | **83** |
| [ai-seo](https://github.com/coreyhaines31/marketingskills/tree/main/skills/ai-seo) | Optimises content to appear in AI-generated answers and LLM search. | `npx skills add coreyhaines31/marketingskills --skill ai-seo` | 31 | 28 | 23 | **82** |
| [launch-strategy](https://github.com/coreyhaines31/marketingskills/tree/main/skills/launch-strategy) | Plans product launches and feature announcements. | `npx skills add coreyhaines31/marketingskills --skill launch-strategy` | 30 | 28 | 23 | **81** |
| [pricing-strategy](https://github.com/coreyhaines31/marketingskills/tree/main/skills/pricing-strategy) | Pricing, packaging and monetisation for SaaS. | `npx skills add coreyhaines31/marketingskills --skill pricing-strategy` | 30 | 28 | 23 | **81** |
| [programmatic-seo](https://github.com/coreyhaines31/marketingskills/tree/main/skills/programmatic-seo) | Designs SEO page templates for content at scale. Pair with Google's spam policies. | `npx skills add coreyhaines31/marketingskills --skill programmatic-seo` | 29 | 28 | 22 | **79** |
| [copywriting](https://github.com/coreyhaines31/marketingskills/tree/main/skills/copywriting) | Writes landing page, homepage and ad copy. | `npx skills add coreyhaines31/marketingskills --skill copywriting` | 28 | 28 | 22 | **78** |
| [Product-Manager-Skills](https://github.com/deanpeters/Product-Manager-Skills) | Discovery, prioritisation, PRDs, roadmaps and SaaS metrics. | see repo | 28 | 27 | 22 | **77** |

### Skill authoring and tooling

| Skill | What it does and when to use it | Install / source | P | D | I | Score |
|---|---|---|---|---|---|---|
| [writing-skills](https://github.com/obra/superpowers/tree/main/skills/writing-skills) | Writes and tests new skills using a TDD-style loop. | `npx skills add obra/superpowers --skill writing-skills` | 34 | 32 | 23 | **89** |
| [agnix](https://github.com/avifenesh/agnix) | Linter for SKILL.md, CLAUDE.md, hooks and MCP configs, with auto-fix and an LSP server. | see repo | 33 | 25 | 23 | **81** |
| [review-claudemd](https://github.com/ykdojo/claude-code-tips/tree/main/skills/review-claudemd) | Reviews recent sessions to suggest CLAUDE.md improvements. | see repo | 31 | 26 | 23 | **80** |
| [SkillCheck-Free](https://github.com/olgasafonova/SkillCheck-Free) | Free SKILL.md validator with 30+ structure, naming and semantic checks. | see repo | 31 | 24 | 23 | **78** |
| [template](https://github.com/anthropics/skills/tree/main/template) | Minimal official skeleton for a new skill. | copy folder | 25 | 31 | 22 | **78** |

### Also reviewed (official, situational)

These are legitimate, maintained skills that scored 75 to 84 but serve a narrower audience. Install only if you use the product.

| Skill | What it does | Source | Score |
|---|---|---|---|
| algorithmic-art | Generative art with p5.js and seeded randomness. | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/algorithmic-art) | **76** |
| brand-guidelines | Applies brand colours and typography; a pattern to copy for your own brand. | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/brand-guidelines) | **75** |
| slack-gif-creator | Animated GIFs sized for Slack. | [anthropics/skills](https://github.com/anthropics/skills/tree/main/skills/slack-gif-creator) | **75** |
| gh-address-comments (OpenAI) | Addresses PR review comments via the GitHub CLI. | [officialskills.sh](https://officialskills.sh/openai/skills/gh-address-comments) | **84** |
| playwright (OpenAI) | Real browser automation for navigation, forms and scraping. | [officialskills.sh](https://officialskills.sh/openai/skills/playwright) | **82** |
| figma-use | Prerequisite for Figma Plugin API canvas writes. | [officialskills.sh](https://officialskills.sh/figma/skills/figma-use) | **78** |
| apollo-federation | Federation 2 subgraphs and supergraph composition. | [officialskills.sh](https://officialskills.sh/apollographql/skills/apollo-federation) | **78** |
| terraform-stacks (HashiCorp) | Multi-environment, multi-region infrastructure. | [officialskills.sh](https://officialskills.sh/hashicorp/skills/terraform-stacks) | **77** |
| agents-sdk (Cloudflare) | Stateful AI agents with scheduling, RPC and MCP. | [officialskills.sh](https://officialskills.sh/cloudflare/skills/agents-sdk) | **81** |
| sandbox-sdk (Cloudflare) | Isolated code execution on Workers. | [officialskills.sh](https://officialskills.sh/cloudflare/skills/sandbox-sdk) | **78** |
| netlify-edge-functions | Edge middleware and geolocation logic. | [officialskills.sh](https://officialskills.sh/netlify/skills/netlify-edge-functions) | **76** |
| expo-cicd-workflows | CI/CD for Expo projects. | [officialskills.sh](https://officialskills.sh/expo/skills/expo-cicd-workflows) | **78** |
| sentry-react-native-sdk | Sentry for React Native and Expo. | [officialskills.sh](https://officialskills.sh/getsentry/skills/sentry-react-native-sdk) | **80** |
| sentry-node-sdk | Sentry for Node.js, Bun and Deno. | [officialskills.sh](https://officialskills.sh/getsentry/skills/sentry-node-sdk) | **80** |
| sentry-create-alert | Alerts routed to email, Slack, PagerDuty and more. | [officialskills.sh](https://officialskills.sh/getsentry/skills/sentry-create-alert) | **77** |
| hugging-face-evaluation | Model evaluation with vLLM and lighteval. | [officialskills.sh](https://officialskills.sh/huggingface/skills/hugging-face-evaluation) | **77** |
| neon-postgres-egress-optimizer | Reduces Neon egress and data transfer. | [officialskills.sh](https://officialskills.sh/neondatabase/skills/neon-postgres-egress-optimizer) | **76** |
| better-auth twoFactor | Two-factor auth with Better Auth. | [officialskills.sh](https://officialskills.sh/better-auth/skills/twoFactor) | **78** |
| auth0-mfa | Adds MFA to Auth0-powered apps. | [officialskills.sh](https://officialskills.sh/auth0/skills/auth0-mfa) | **78** |
| auth0-react-native | Auth0 for React Native and Expo. | [officialskills.sh](https://officialskills.sh/auth0/skills/auth0-react-native) | **77** |
| selenium-skill (TestMu) | Selenium WebDriver tests in six languages. | [LambdaTest/agent-skills](https://github.com/LambdaTest/agent-skills/tree/main/selenium-skill) | **79** |
| appium-skill (TestMu) | Appium mobile automation for Android and iOS. | [LambdaTest/agent-skills](https://github.com/LambdaTest/agent-skills/tree/main/appium-skill) | **78** |
| junit-5-skill (TestMu) | JUnit 5 tests in Java with Mockito. | [LambdaTest/agent-skills](https://github.com/LambdaTest/agent-skills/tree/main/junit-5-skill) | **78** |
| wp-rest-api (WordPress) | WordPress REST routes, schema and auth. | [officialskills.sh](https://officialskills.sh/WordPress/skills/wp-rest-api) | **76** |
| churn-prevention | Cancellation flows, save offers, failed-payment recovery. | [marketingskills](https://github.com/coreyhaines31/marketingskills/tree/main/skills/churn-prevention) | **77** |
| onboarding-cro | Post-signup activation and time-to-value. | [marketingskills](https://github.com/coreyhaines31/marketingskills/tree/main/skills/onboarding-cro) | **77** |
| competitor-alternatives | Comparison and alternative landing pages for SEO. | [marketingskills](https://github.com/coreyhaines31/marketingskills/tree/main/skills/competitor-alternatives) | **76** |
| linear-cli-skill | Teaches the agent to use a Linear CLI instead of an MCP server. | [Valian/linear-cli-skill](https://github.com/Valian/linear-cli-skill) | **75** |
| gh-star-history | Charts and compares GitHub star history. | [ykdojo/gh-star-history](https://github.com/ykdojo/gh-star-history) | **75** |
| Claude Code Video Toolkit | Video production with Remotion, ElevenLabs, FFmpeg and Playwright. | [digitalsamba/claude-code-video-toolkit](https://github.com/digitalsamba/claude-code-video-toolkit) | **75** |

---

## Safety checklist before you install

A skill runs with your agent's full permissions: shell, file system and any credentials in your environment. Treat every install as a code review.

1. **Prefer official and proven sources.** Vendor teams (Anthropic, Vercel, Cloudflare, Trail of Bits, Sentry, Stripe, Google, Microsoft) and long-maintained community repos first.
2. **Read every file in the folder**, not only `SKILL.md`. Scripts are where risky behaviour hides.
3. **Grep for red flags:** "ignore previous instructions", "do not tell the user", "do not mention", conditions based on who is asking, and `curl ... | bash` in install steps.
4. **Watch network traffic** on first run. Any unexplained outbound call is a potential exfiltration path.
5. **Restrict tools.** Use `allowed-tools` in frontmatter and a deny list in `.claude/settings.json` that includes `.env`. Use hooks for guarantees; a skill is an instruction, a hook is enforcement.
6. **Pin versions** for fast-moving repos, and re-review on update.
7. **Keep the installed set small** so reviewing it stays realistic.

---

## FAQ

**What are Claude Skills?**
Reusable folders of instructions, scripts and resources (`SKILL.md` plus optional files) that Claude loads only when a task needs them. Anthropic introduced them in October 2025 and published Agent Skills as an open standard.

**How do I install a Claude skill in Claude Code?**
Use `npx skills add <owner>/<repo> --skill <name>`, the `/plugin` marketplace, or copy the folder into `~/.claude/skills/` or `.claude/skills/`. Then restart the session. See [Quick start](#quick-start-install-and-use-any-skill).

**Do these skills work in Cursor, Codex or Gemini CLI?**
Most do, because they follow the open Agent Skills format. Skills that call Claude-specific tools or plugins may need small changes.

**Skills vs MCP vs subagents vs hooks: which do I need?**
Skills are knowledge and procedure. MCP servers add capabilities (a database, a browser). Subagents isolate context for heavy or parallel work. Hooks are deterministic code that always runs. Use a hook when you need a guarantee.

**How many skills should I install?**
As few as solve your real problems. Too many dilute matching and can exceed the description budget, which silently drops skills.

**Why does my skill not trigger?**
Usually a vague description. Write it as a trigger ("Use when writing a git commit message for staged changes"), front-load the key words, and check `/doctor` for budget overflow.

**Are these skills free?**
Yes, all are free to install. Skills marked 🔑 need an account or API key with the vendor to be useful.

**Can I copy these skills into my own repo?**
Check each licence. Anthropic's document skills (docx, pdf, pptx, xlsx) are source-available, not open source. This list links to sources and never redistributes skill files.

---

## Contributing

Suggest a skill by opening an issue with the template in [CONTRIBUTING.md](CONTRIBUTING.md). Every submission is scored against the same rubric and must pass the hard gates. We do not accept payment for inclusion or ranking, and we do not include affiliate links.

## License

The list text is released under [CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Each skill keeps its own licence, set by its authors.

**Keywords:** Claude skills, Claude Code skills, Agent Skills, SKILL.md, best Claude skills 2026, Claude Code plugins, awesome Claude skills, Anthropic skills, Codex skills, Cursor skills, AI coding agent skills.
