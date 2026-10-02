---
name: tdd-first
description: Enforces strict Test-Driven Development (TDD) and the Red-Green-Refactor cycle. Mandates writing failing tests before any feature, bug fix, or business logic implementation is generated.
---

# Test-Driven Development (TDD) Enforcer

## Goal
Eliminate untested logic and post-hoc, tautological tests by enforcing a strict **Red-Green-Refactor** development cycle. The AI agent must never write production implementation code without first authoring a failing test that validates the requirement.

---

## The Red-Green-Refactor Protocol

### 1. 🔴 RED: Write a Failing Test First
* **Rule:** Before writing or modifying any function, service, or business logic, write a unit or integration test specifying expected inputs, outputs, and behaviors.
* **Execution:**
  * Define the test file using the project's testing framework (e.g., Vitest, Jest, Pytest, Go testing).
  * Assert expected return values, state changes, or thrown exceptions.
  * Execute or mentally verify that the test fails *specifically* because the implementation does not yet exist or satisfy the condition—not due to invalid test syntax.

### 2. 🟢 GREEN: Write Minimal Implementation
* **Rule:** Write only the minimal amount of production code required to satisfy the failing test.
* **Prohibition:** Do not implement speculative features, unrequested configurations, or premature abstractions not covered by tests.
* **Execution:** Re-run the test suite to confirm the target test passes cleanly.

### 3. 🔵 REFACTOR: Clean Architecture & Optimization
* **Rule:** Once tests are green, refactor code to eliminate duplication, enhance readability, and comply with SOLID/DRY principles.
* **Execution:** Re-run the tests to guarantee that refactoring preserved all functional contracts.

---

## Non-Negotiable Testing Standards

### 1. Edge Case Coverage
Happy-path tests alone are strictly unacceptable. Every feature must include tests for:
* **Boundary Conditions:** Empty arrays, blank strings, zero, negative numbers, maximum thresholds.
* **Nullability & Missing Data:** `null`, `undefined`, incomplete payloads, or malformed data structures.
* **Error Paths:** Invalid inputs must trigger expected domain errors, HTTP error codes, or thrown exceptions.
* **Async & Race States:** Timeouts, rejected promises, network failures, or concurrent calls where applicable.

### 2. Zero-Tolerance Rules
* **No Post-Hoc Tests:** Writing implementation code first and back-filling tests afterwards is forbidden.
* **No Tautological Tests:** Never write tests that test mocks against mocks without executing actual business logic.
* **No Assertion Tampering:** Never comment out, weaken, or delete existing tests to force a green build. If existing tests break, investigate whether it is an intentional contract change or a regression.

---

## Execution Instructions for the Agent

1. **Discover Test Environment:**
   * Scan `package.json`, `pyproject.toml`, `go.mod`, or workspace config to identify the active test runner (Vitest, Jest, Playwright, Pytest, etc.).
2. **Draft the Specification Test:**
   * Place the test in the designated test folder (`tests/`, `__tests__/`, or co-located `*.test.ts` / `*_test.py`).
   * Clearly describe the behavior in test names (e.g., `it("should reject payments when user balance is insufficient")`).
3. **Execute & Verify Red:**
   * Run the test command to confirm failure:
     ```bash
     npm test -- path/to/test.spec.ts  # or pytest path/to/test.py
     ```
4. **Implement & Verify Green:**
   * Write the implementation code.
   * Re-run the test to confirm it passes.
5. **Report to User:**
   * Clearly present the test cases added, the test execution result (failing -> passing), and any refactoring applied.
