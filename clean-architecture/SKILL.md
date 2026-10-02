---
name: clean-architecture
description: Enforces DRY and SOLID design principles during code generation, refactoring, and architectural design. Use when writing, reviewing, or updating source code.
---

# Clean Architecture (DRY & SOLID)

## Goal
Ensure all generated, edited, or refactored code minimizes duplication and adheres strictly to the five SOLID design principles.

## Core Rules

### 1. DRY (Don't Repeat Yourself)
* Actively scan the workspace or file context for existing abstractions, utilities, or components before writing new logic.
* Extract repeating patterns, formulas, or structural code blocks into reusable, single-source-of-truth functions, hooks, or modules.

### 2. SOLID Principles
* **Single Responsibility (SRP):** Every class, module, or function must have exactly one reason to change. Break down bloated multi-purpose files into granular, focused units.
* **Open/Closed (OCP):** Software entities should be open for extension, but closed for modification. Prefer polymorphism, configuration objects, or composition over long, hardcoded `switch` or `if/else` chains.
* **Liskov Substitution (LSP):** Subtypes must be substitutable for their base types without altering correctness. Ensure interfaces and extensions strictly honor parent contracts.
* **Interface Segregation (ISP):** Clients should not be forced to depend on methods they do not use. Prefer small, focused interfaces/types over large, generic ones.
* **Dependency Inversion (DIP):** Depend on abstractions, not concretions. Inject dependencies rather than hardcoding imports of concrete implementations where structural flexibility is needed.

## When to use this skill
* When a user asks to "write," "create," "implement," or "refactor" logic.
* When managing architectural layouts, directory setups, or object-oriented design.

## Instructions
1. **Analyze:** Before writing any file, review the proposed structure against SRP and DRY rules.
2. **Refactor First:** If a requested feature causes code duplication, explicitly suggest or execute a refactoring step to extract the shared logic first.
3. **Verify:** Before finalizing the response or file write, run a mental checklist ensuring no single class or module violates any part of SOLID.