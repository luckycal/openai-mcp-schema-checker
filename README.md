OpenAI Schema Checker

OpenAI’s Structured Outputs and strict tool schemas are based on JSON Schema, but they intentionally support only a constrained subset. As a result, a schema that is perfectly valid according to the JSON Schema specification may still be a poor fit for OpenAI’s tool-calling APIs or trigger reviewer feedback.

The problem is that existing JSON Schema validators answer the wrong question:

“Is this valid JSON Schema?”

What developers really need to know is:

“Will this work well with OpenAI’s strict tool-calling implementation?”

OpenAI Schema Checker is a browser-based linter and playground that analyzes schemas specifically through the lens of OpenAI’s Structured Outputs and strict tool requirements.

It identifies three classes of issues:

* Errors — Constructs that violate OpenAI’s strict schema requirements (for example, missing additionalProperties: false on objects).
* Warnings — Valid JSON Schema that doesn’t map well to OpenAI’s preferred schema subset or constrained decoding (for example, minProperties, oneOf, conditional schemas, or optional object properties).
* Reviewer Risks — Schema patterns that are technically valid but frequently lead to confusing synthesized tool signatures or poor tool selection by language models.

Unlike a generic validator, the checker explains why each issue matters, links it back to OpenAI’s documented constraints where possible, and suggests practical rewrites.

Features

* Local-only, single-page application
* No server or account required
* Schemas never leave your browser
* Persistent history using IndexedDB
* Upload, edit, lint, and compare schemas
* Actionable fix suggestions
* OpenAI-specific compatibility checks rather than generic JSON Schema validation

Why this exists

There is currently an ecosystem gap between JSON Schema tooling and OpenAI tool development.

A schema can be:

* valid JSON Schema,
* accepted by OpenAI,
* yet still produce an awkward or ambiguous tool signature that makes it harder for the model to call correctly.

This checker helps developers identify those issues before they become debugging sessions.
A browser-based linter for OpenAI strict tool schemas. Finds compatibility issues that generic JSON Schema validators miss, including strict-mode violations, reviewer risks, and model-unfriendly schema patterns. Runs entirely locally—your schemas never leave your browser.
