---
name: frontend-blueprint
description: Enforces the use of React, Vite, the latest Tailwind CSS, and Atomic Design component architecture for new project scaffolding or frontend development. Automatically initializes Git hooks via Husky. Keeps the backend framework unopinionated.
---

# Project Scaffolding & UI Blueprint

## Goal
Whenever the user requests a new project setup, app creation, or frontend UI components, automatically adopt React, Vite, Tailwind CSS (v4+), and Atomic Design system principles. Ensure Husky is configured for quality control.

## Frontend Stack & Directory Requirements
* **Build Tool:** Vite
* **Framework:** React (TypeScript preferred)
* **Styling:** Tailwind CSS (Latest Version). Handle configurations directly via CSS variables and `@theme` directives in the main CSS entry point. Do NOT generate a legacy `tailwind.config.js`.

## Component Architecture (Atomic Design)
Organize the frontend component directory layout (`src/components/`) strictly following Atomic Design principles:
* **Atoms:** Basic building blocks that cannot be broken down further (e.g., `Button`, `Input`, `Label`, `Badge`).
* **Molecules:** Combinations of atoms bonded together to form a simple functional unit (e.g., `SearchBar` = Input + Button, `FormField` = Label + Input).
* **Organisms:** Complex UI components composed of molecules and/or atoms. They form distinct, reusable sections of the interface (e.g., `Navbar`, `Sidebar`, `ProductCardGrid`, `CommentSection`).
* **Templates:** Page-level layouts that place components into a semantic structure, focusing on content allocation rather than specific data binding (e.g., `DashboardLayout`).
* **Pages:** Specific view instances that inject concrete data into templates and manage localized application state.

## Git Automation & Quality Control (Husky)
* **Initialization:** Automatically initialize Git (`git init`) before setting up tooling dependencies.
* **Husky Setup:** Install Husky as a development dependency and run `npx husky init`.
* **Hooks Configuration:** Configure a default `.husky/pre-commit` hook that triggers frontend linting and type checking (e.g., `npm run lint` or `tsc --noEmit`). Ensure the `prepare` script is added to `package.json`.

## Backend Architecture
* Do NOT assume or force any specific backend framework by default. Leave the backend entirely open-ended until explicit instructions are given by the user.

## Instructions for Execution
1. **Initialize Workspace:** Run git initialization, then outline a standard root workspace directory containing a dedicated `frontend/` directory built around Vite's structure.
2. **Apply Atomic Folders:** Inside `src/`, generate empty stub directories or initial index targets for `components/atoms`, `components/molecules`, `components/organisms`, `templates`, and `pages`.
3. **Graceful Prompting:** Present the completed project structure to the user, confirm that Husky hooks are armed, and ask how they would like to handle the backend architecture.