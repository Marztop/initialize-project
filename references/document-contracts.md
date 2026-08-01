# Initialization Document Contracts

## Target structure

Keep Agent-discoverable behavior rules at the project root and initialization material in the hidden control directory:

```text
<project-root>/
|-- AGENTS.md
`-- .init_repo/
    |-- design/
    |   `-- design_doc.md
    |-- research/
    `-- records/
```

Create `design/stages/`, `design/adr/`, and `records/stages/` only when they have content.

Do not relocate project assets into `.init_repo/`. Source code, tests, tools, dependency manifests, build configuration, and user-facing documentation must follow the target project's conventions.

## Root AGENTS.md

Create a concise operating contract. Include only rules that guide future Agent behavior:

- scope and precedence of the file;
- requirement to read `.init_repo/design/design_doc.md` before architecture or technical-selection work when that file exists;
- statement that `design_doc.md` is the source of truth for project goals, technical choices, architecture, runtime plan, and delivery roadmap;
- instruction not to replace confirmed frameworks, databases, package managers, runtime plans, or architectural boundaries without user approval;
- dependency-change confirmation boundaries;
- secret and local-machine-data safeguards;
- validation and delivery-record expectations;
- instruction to keep project assets in the project's normal locations;
- user instructions take precedence over generated conventions.

Do not duplicate stack versions, selection rationale, stage plans, or feature requirements in `AGENTS.md`. If a technical decision needs enforcement, state only the behavioral constraint and point to `design_doc.md`.

For an existing `AGENTS.md`, preserve wording, structure, and scope. Append only user-approved project-wide conventions. Do not add generated headings merely to make the file resemble a template.

## design/design_doc.md

Write confirmed project-specific content, not empty prompts. Preserve existing content during incremental initialization.

Cover:

1. project objective and success criteria;
2. target users and core scenarios;
3. scope and explicit non-goals;
4. current state and constraints;
5. technical choices, rationale, architecture, and module boundaries;
6. runtime and dependency plan, including versions, creation and activation commands, and dependency entry points;
7. project-asset layout;
8. testing and acceptance strategy;
9. delivery-stage roadmap;
10. links to authoritative existing documents;
11. unresolved questions, if any.

The stage roadmap records each confirmed stage's objective, scope, non-goals, dependencies, deliverables, acceptance criteria, and risks.

## Stage lifecycle

- Keep the complete roadmap in `design/design_doc.md`.
- Before starting a stage, create `design/stages/<nn>-<slug>.md` only when task-level design is needed.
- On completion, create `records/stages/<nn>-<slug>.md` with delivered scope, validation evidence, deviations, remaining issues, and conclusion.
- Never pre-create detailed files for all future stages.

## Research and records

Use `research/` for verified external facts, dependency investigations, protocol notes, and experiment conclusions. Cite sources or commands where they materially support a decision.

Use `records/` for implementation history, fixes, validation results, and stage completion reports. Promote durable behavior rules to `AGENTS.md` only after user approval; keep architectural rationale in design material and reusable facts in research.

## Existing material and language

- Read existing `README*`, `docs/`, ADRs, design notes, and operational instructions as evidence.
- Link to authoritative material; do not move, rename, translate, or duplicate it automatically.
- Surface contradictions and ask which source reflects the current project.
- Use the user's current language for new files.
- Preserve an existing document's main language during incremental edits.
- Keep APIs, commands, paths, identifiers, package names, model names, and original errors unchanged.
