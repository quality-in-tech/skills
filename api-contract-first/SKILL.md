---
name: api-contract-first
description: Enforces a single source of truth for API schemas (OpenAPI, Zod, tRPC) before writing endpoints or client code. Prevents fullstack type drift and prohibits untyped network calls.
---

# API Contract-First Development

## Goal
Prevent client-server drift, runtime type mismatches, and undocumented endpoints by requiring a single, type-safe API contract (Zod, OpenAPI, tRPC, or Protocol Buffers) to be authored and validated **before** implementing backend route handlers or frontend consumption logic.

---

## Core Contract Rules

### 1. Single Source of Truth
* All client-server communication must derive from a single, centralized schema definition.
* **Accepted Standards:**
  * **TypeScript / Fullstack:** Shared Zod / Valibot / TypeBox schemas or tRPC routers.
  * **REST / Polyglot:** OpenAPI 3.x / Swagger specifications (`openapi.yaml` / `openapi.json`).
  * **RPC / Microservices:** Protocol Buffers (`.proto`) or gRPC schemas.
  * **GraphQL:** Strongly typed schema definitions (`.graphql`).
* Prohibit inline, ad-hoc TypeScript interfaces duplicated separately in frontend and backend folders.

### 2. Define Contract Before Implementation
* **Step 1:** Author or update the contract specification (request params, query strings, headers, request body, and success/error response bodies).
* **Step 2:** Generate or infer types directly from the schema (e.g., `z.infer<typeof CreateUserPayload>`).
* **Step 3:** Implement server route handlers that validate incoming payloads against the contract (e.g., parsing request body through schema validation middleware).
* **Step 4:** Implement frontend API clients, React Query / SWR hooks, or state actions consuming the inferred types.

### 3. Prohibition of Untyped Network Calls
* **No `any` Returns:** Never write `const data = (await res.json()) as any`. Data must be validated against the schema or typed via inferred return types.
* **No Bare `fetch()`:** Raw, untyped `fetch()` calls without schema validation wrappers or generated client SDKs are prohibited.
* **No Unchecked Query Params:** All query parameters and route parameters (`req.params`) must be parsed and coerced through schema types (e.g., string to integer conversion).

### 4. Explicit Error Contracts
* Contracts must define error envelopes in addition to successful payloads.
* Standardize on consistent error formats (e.g., RFC 7807 Problem Details or `{ error: string, code: string, details?: unknown }`).
* Ensure client code is forced to handle 4xx validation errors and 5xx failure states gracefully.

### 5. Backward Compatibility & Non-Breaking Evolution
* When modifying an existing contract:
  * Adding fields must default to optional or provide sensible fallback defaults.
  * Renaming or removing fields requires formal API versioning (e.g., `/api/v2/...`) or deprecation warnings to avoid breaking deployed clients.

---

## Instructions for Execution

1. **Locate Shared Contract Directory:**
   * Identify or create the shared contract directory (e.g., `src/shared/contracts/`, `packages/contracts/`, or `api/spec/`).
2. **Author the Schema Contract:**
   * Write explicit validation constraints (e.g., string lengths, regex patterns, email validations, enum values).
   * Export both the runtime validator and the static TypeScript types:
     ```typescript
     export const UserProfileSchema = z.object({
       id: z.string().uuid(),
       email: z.string().email(),
       role: z.enum(["admin", "member", "guest"]),
     });
     export type UserProfile = z.infer<typeof UserProfileSchema>;
     ```
3. **Mount Backend Route Validation:**
   * Ensure the controller rejects invalid payloads with HTTP 400 or 422 before executing database or business logic.
4. **Wire Frontend Integration:**
   * Import the shared contract or type in client API services or query hooks.
5. **Verify Bidirectional Integrity:**
   * Confirm that modifying a contract field produces immediate type-check errors in both frontend and backend until both sides are updated.
