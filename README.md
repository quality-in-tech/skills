# QInT Skills ⚡

[![License](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](LICENSE)
[![Website](https://img.shields.io/badge/Website-quality--int.com-blue?style=flat&logo=googlechrome&logoColor=white)](https://quality-int.com/)
[![Book a Call](https://img.shields.io/badge/Book%20a%20Call-Calendar-success?style=flat&logo=googlecalendar&logoColor=white)](https://calendar.app.google/76JmSruMAY151qB59)
[![Organization](https://img.shields.io/badge/Maintained%20by-Quality%20Insight%20Tech-0052CC.svg)](https://github.com/quality-in-tech)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](https://github.com/quality-in-tech/skills/pulls)

> **Production-grade AI agent skills and architectural guardrails by Quality Insight Tech (QInT).**  
> Eliminate AI technical debt, enforce software craftsmanship, and build maintainable systems from day one.

---

## 💡 Why QInT Skills?

AI coding assistants generate code faster than ever. However, without strict guardrails, standard LLM code generation quickly leads to **architectural drift**, **duplicated logic**, and **unmaintainable spaghetti code**.

At **Quality Insight Tech (QInT)**, we believe AI should accelerate craftsmanship, not compromise it. 

This repository contains our curated, battle-tested skills designed for agentic coding environments (such as Antigravity, Cursor, Claude Code, and other LLM developer workflows). Each skill equips the AI agent with specific behavioral rules, architectural constraints, and automated quality controls.

---

## 📦 Skills Catalog

| Skill | Purpose | Key Guardrails |
| :--- | :--- | :--- |
| [**`clean-architecture`**](./clean-architecture/SKILL.md) | Enforce DRY & SOLID principles | SRP, OCP, LSP, ISP, DIP compliance; proactive refactoring of duplicated logic. |
| [**`frontend-blueprint`**](./frontend-blueprint/SKILL.md) | Modern frontend scaffolding & quality | React + Vite + Tailwind CSS v4, strict Atomic Design hierarchy, Husky pre-commit hooks. |
| [**`tdd-first`**](./tdd-first/SKILL.md) | Test-Driven Development (TDD) enforcer | Strict Red-Green-Refactor cycle, failing test required before implementation, boundary edge-case coverage. |
| [**`api-contract-first`**](./api-contract-first/SKILL.md) | Type-safe API contracts & zero drift | Centralized schema single source of truth (Zod/OpenAPI/tRPC), eliminates untyped `any` and unvalidated endpoints. |

---

## 🚀 How to Use

### 1. Direct Workspace Integration
Clone or copy the skills directly into your project's agent configuration directory:

```bash
# Clone the repository
git clone https://github.com/quality-in-tech/skills.git

# Copy desired skills into your workspace's skill directory
cp -r skills/clean-architecture /path/to/your/project/.agent/skills/
cp -r skills/frontend-blueprint /path/to/your/project/.agent/skills/
```

### 2. Global Agent Configuration
If your agentic assistant supports global skill discovery (e.g. Antigravity or custom agent CLI runners), symlink or clone this repository into your global skills path:

```bash
# Example for Antigravity or compatible agent runners:
git clone https://github.com/quality-in-tech/skills.git ~/.gemini/antigravity/skills/qint-skills
```

### 3. As a Git Submodule
Keep your team updated with our latest skills by adding this repository as a submodule:

```bash
git submodule add https://github.com/quality-in-tech/skills.git .skills
```

---

## 🛠️ The QInT Engineering Standard

Every skill in this repository is designed around three non-negotiables:

1. **Zero Unintentional Technical Debt:** AI agents must check for existing abstractions before introducing new ones.
2. **Defensive Quality Gates:** Quality checks (linting, type safety, pre-commit hooks) must be armed from commit zero.
3. **Architectural Consistency:** Predictable component and module structures that scale gracefully from prototype to enterprise grade.

---

## 🤝 Partner with Quality Insight Tech (QInT)

Are you looking to scale your engineering team or build high-performance products without accumulating technical debt?

At **Quality Insight Tech (QInT)**, we partner with startups and enterprise teams to deliver:
* **Custom Software Engineering:** Full-lifecycle development of robust web, mobile, and cloud platforms.
* **AI Workflow & Agentic Architecture:** Implementing secure, reliable AI-assisted workflows and agent systems that adhere to enterprise engineering standards.
* **Architecture & Codebase Audits:** Evaluating code quality, security boundaries, and scalability bottlenecks to future-proof your systems.

📫 **Let’s build something great together:**
* 🌐 **Website:** [quality-int.com](https://quality-int.com/)
* 📅 **Schedule a Call:** [Book a Discovery Call](https://calendar.app.google/76JmSruMAY151qB59)
* 🐙 **GitHub:** [@quality-in-tech](https://github.com/quality-in-tech)
* 💬 **Consulting & Inquiries:** Connect with our team to discuss custom engineering, codebase audits, or AI agent workflow implementations.

---

## 📄 License

Distributed under the Apache 2.0 License. See [`LICENSE`](LICENSE) for details.
