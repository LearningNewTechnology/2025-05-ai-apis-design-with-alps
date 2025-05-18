
# 📍 Project Roadmap: ALPS-Driven Development Pipeline

This roadmap outlines four next-phase capabilities built on your ALPS documentation and conversion foundation.

---

## ✅ Stage 1: ALPS from User Story

**Goal**: Convert user stories into structured ALPS descriptors.

### Inputs:
- User stories written in natural language
- Classification rules from Operational Notes

### Actions:
- Parse verbs into transition descriptors (`safe`, `unsafe`, `idempotent`)
- Extract nouns and attributes into `semantic` descriptors
- Use tags to group descriptors by role or domain
- Generate `descriptor[]` arrays for application states

### Output:
- A valid ALPS JSON profile

---

## 🔐 Stage 2: Generate Security Profile from ALPS

**Goal**: Define and associate roles/permissions with transitions and data.

### Inputs:
- ALPS descriptor list with `id`, `tag`, `type`

### Actions:
- Create a `security-profile.json` or `.yaml`
- Map:
  - `transition.id` or `tag` → role or permission
  - Data fields → access scope
- Define enforcement logic (public, admin-only, etc.)

### Output:
- A standalone security profile for use in docs, OpenAPI, or enforcement layers

---

## 🧪 Stage 3: Generate NodeJS Tests from ALPS

**Goal**: Generate test suites for transitions using NodeJS (e.g. with `supertest`, `tap`, or `jest`).

### Inputs:
- ALPS profile
- Payload generation rules

### Actions:
- For each transition:
  - Infer HTTP method from `type` and `id`
  - Generate input payloads (query string or JSON body)
  - Build `describe()` and `it()` blocks for testing
- Include response validation (e.g. 200, 404, 403)

### Output:
- Auto-generated `*.test.js` files
- Optionally scaffolded project (npm-ready)

---

## 🔁 Stage 4: Convert ALPS to OpenAPI

**Goal**: Translate the ALPS model into a compliant OpenAPI 3.1 spec.

### Inputs:
- ALPS JSON profile

### Actions:
- Map transitions to OpenAPI `paths` and `operations`
- Convert `descriptor` fields into `parameters` or `requestBody`
- Derive `components.schemas` from `semantic` descriptors
- Use `rt` to assign `responses`

### Output:
- A full `openapi.yaml` file
- Optionally bundled with generated client SDKs or docs

---

## 📂 Optional Shared Assets

- `alps-to-html-step-by-step.md`
- `alps-html-operational-notes.md`
- `llms-full.txt` (ALPS base spec)
- `alps-html-style-guide.md` (optional extract)

---

## 🧠 Suggested Order of Work

1. ✅ Finalize ALPS profile from user stories
2. ✅ Convert to HTML for visual confirmation
3. 🔐 Generate security overlays
4. 🧪 Create NodeJS tests
5. 🔁 Convert to OpenAPI for public interface

---

## 💾 Future Enhancements

- ALPS-aware CLI tool
- Editor plugin for visual ALPS building
- HTML+Mermaid viewer with embedded payload preview

