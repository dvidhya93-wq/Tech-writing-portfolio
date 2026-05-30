# Prompt Engineering & Technical Writing

## Project: API Documentation Generation


**Category:** Prompt Engineering · Technical Writing  
**Tool:** Claude (Sonnet 4.6)  
**Output Format:** Markdown (`.md`)

---

## Overview

This project demonstrates how constraint tuning in prompts directly shapes AI output quality and scope. The same raw API input was run through two different prompts to show how prompt engineering decisions control inference, completeness, and accuracy.

- Prompt 1 (Permissive)
- Prompt 2 (Restrictive) 

---

## Same Input. Two Prompts. Two Different Outputs.

Input - A single unstructured sentence with no formatting, field types, examples, error codes, or edge cases.

> **Raw Input (identical for both prompts)** 
> "API to start scan POST /scan/start with target url and scan type returns scan id and status queued api key required."

---


## Prompts Comparison

| Dimension              | Prompt 1 (Permissive)                              | Prompt 2 (Restrictive)                          |
|------------------------|----------------------------------------------------|-------------------------------------------------|
| **Sections generated** | 9 of 9                                             | 7 of 9 (Error Codes & Notes removed)           |
| **Authentication**     | Header name, format, failure code inferred         | One-line statement only                         |
| **Request example**    | Full `curl` with auth header                       | Plain HTTP block, no auth                       |
| **Response fields**    | 5 fields with types + table                        | 2 fields only (`scan_id`, `status`)             |
| **Error codes**        | 5 codes with descriptions                          | Not generated (not in input)                    |
| **Notes / edge cases** | 5 (polling, idempotency, rate limits, etc.)        | Not generated (not in input)                    |
| **Inference level**    | High — fills gaps using REST conventions           | None — strictly input-bound                     |
| **Best suited for**    | First-draft docs, greenfield APIs                  | Strict accuracy, auditable, compliance contexts |

---

## Prompt Engineering Breakdown

### Techniques Used (Both Prompts)

**1. Role Priming**  
`"Act as a senior technical writer"` anchors vocabulary, structure, and judgment to professional documentation standards.

**2. Explicit Structure Scaffolding**  
Listing each section in order gives the model a skeleton to fill — preventing collapsed or missing sections.

**3. Constraint Layering**  
Conciseness, tone, and format constraints operate independently from content rules, shaping style without affecting what information is used.

### What Changed in Prompt 2

Three additional constraints were added:

| Constraint                                        | Effect                                                             |
|---------------------------------------------------|--------------------------------------------------------------------|
| `Use only the information provided in the input`  | Blocked all REST convention inference                              |
| `Do not include any additional information`       | Prevented enriched examples (curl, auth headers, extra fields)     |
| `Remove sections if information is not available` | Dropped Error Codes and Notes entirely                             |

These constraints shifted the model from a *creative generator* to a *faithful transcriber* — a critical distinction for documentation accuracy.

---

## Key Takeaways

- **Constraints are precision tools.** Adding three lines to a prompt produced a fundamentally different document — not just in length, but in reliability and intent.
- **Permissive prompts are faster for drafting.** Prompt 1 is ideal when you want a complete first draft to edit down.
- **Restrictive prompts are safer for accuracy.** Prompt 2 is ideal when documentation must reflect only verified, source-of-truth information.
- **Neither is universally better** — the right choice depends on whether you need *coverage* or *correctness*.

---

## Skills Demonstrated

- Prompt engineering (role priming, scaffolding, constraint layering, negative constraints)
- REST API documentation standards
- Comparative analysis of AI outputs
- Technical writing for developer audiences
- Markdown formatting

---
