# 🧠 Prompt Template for ALPS Generation from API Story

Use this template when prompting an LLM to convert an API Story into a valid ALPS profile.

---

## 🔶 Prompt Format

```text
Please create an ALPS profile based on the following API Story. This profile should represent a complete and consistent application state design.

* Format: JSON
* Language: English
* Input: API Story describing application purpose, data properties, resources, and actions
* Requirements:
  - All descriptors must have unique IDs
  - Ontology fields must use `type: semantic` and `lowerCamelCase` IDs
  - Resource states must use `UpperCamelCase` IDs and `type: semantic`
  - Operations (choreography) must use `type: safe`, `unsafe`, or `idempotent`
  - Actions should use `go` or `do` prefixes based on type
  - Each operation must specify `rt` (return state) and include field inputs via `href`
  - Tags must be applied consistently for grouping
  - The document must include all necessary fields, states, and transitions
  - The final ALPS must pass a structural verification

API Story:
<INSERT API STORY TEXT HERE>
—or—
Attach the API Story as a file and instruct the LLM to read from the file content.
```

---

## 🔹 Example Invocation

```text
Please create an ALPS profile from the attached file describing a Task Management system. The story includes fields like `title`, `status`, and actions such as `CreateNewTask`, `UpdateStatus`, and `GetFilteredTaskList`. Follow naming conventions and ALPS specification for types, transitions, and field references.
```

---

## ✅ Output Format

- JSON ALPS document
- Includes `$schema` and `alps.version`
- Fully structured: ontology, taxonomy, choreography
- No comments in JSON
