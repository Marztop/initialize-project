---
name: initialize-project
description: Initialize a new or existing software project through an evidence-first, decision-driven interview, then create or incrementally update root AGENTS.md and .init_repo design, research, and delivery records. Use only when the user explicitly asks to initialize, bootstrap, or set up a project, establish project rules and design documentation, or retrofit an existing repository with an initialization structure. Do not trigger for ordinary implementation work or merely because initialization files are missing.
---

# Initialize Project

Establish a confirmed project operating model before implementation begins. Treat initialization as a decision process, not a template copy operation.

## Guardrails

- Act only on an explicit initialization request.
- Inspect the target project before asking questions. Resolve facts from the repository or environment instead of asking the user.
- Ask one unresolved decision at a time. Include a recommended answer and its concrete reason.
- Do not repeat information the user already supplied.
- Do not create or modify target-project files until the user confirms the final initialization summary.
- Do not create environments, install dependencies, change lockfiles, or run implementation stages during initialization.
- Follow the user's language for new documents. Preserve the main language of existing documents and keep technical identifiers in their original form.

## Workflow

### 1. Resolve and inspect the target

Identify the intended project root. If multiple plausible roots exist and the user did not identify one, ask which root to initialize.

Inspect, when present:

- repository state and tracked files;
- every applicable `AGENTS.md`;
- `README*`, `docs/`, ADRs, design notes, and initialization records;
- manifests, lockfiles, runtime-version files, build configuration, test configuration, and source layout;
- current implementation evidence that may contradict documentation.

Use read-only checks. Do not install missing tools or dependencies to complete this inspection.

Classify the target as:

- **new initialization**: no established project operating model exists;
- **incremental initialization**: code, rules, design material, or project conventions already exist.

### 2. Run the initialization interview

Read [interview-guide.md](references/interview-guide.md) before interviewing.

Fill the checklist from discovered facts and the user's request. Ask only about gaps, conflicts, and decisions that materially change the result. When terminology is vague, propose a precise term and confirm it before using it as project language.

Identify any **project-wide working convention**: a durable rule that constrains multiple future tasks or Agent behavior. Keep feature requirements, phase plans, technical selections, and one-off implementation choices out of this category.

For an existing `AGENTS.md`, collect proposed additions without editing the file. Ask whether to append each newly confirmed project-wide working convention.

### 3. Plan delivery stages

Define each stage as an independently acceptable delivery increment, not a timebox or a loose task list.

Propose the complete stage sequence first, explain dependencies and possible parallel work, then confirm each stage with the user. Cover its objective, included scope, non-goals, prerequisites, deliverables, acceptance criteria, and known risks.

### 4. Decide initialization visibility

Ask whether `.init_repo/` should be shared through version control or remain private to the local worktree. Read [version-control.md](references/version-control.md) before proposing or applying this choice.

### 5. Present one final initialization summary

Summarize:

- project objective, users, scenarios, success criteria, scope, and non-goals;
- confirmed technical and runtime plan;
- architecture and project-asset boundaries;
- test and acceptance strategy;
- complete delivery-stage roadmap;
- project-wide working conventions and proposed `AGENTS.md` additions;
- shared or private initialization visibility;
- exact files to create or update.

Call out unresolved conflicts. Ask for one explicit confirmation to materialize this proposal. If the user changes anything, update the summary and ask again.

### 6. Materialize the confirmed model

Read [document-contracts.md](references/document-contracts.md) before writing.

- Create root `AGENTS.md` only when it does not exist.
- Update an existing `AGENTS.md` only with additions the user explicitly approved. Preserve its structure and language.
- Create or incrementally update `.init_repo/design/design_doc.md` as the source of truth for project facts and decisions.
- Create `.init_repo/research/` and `.init_repo/records/` according to the selected version-control mode.
- Do not move, rename, or duplicate existing project documentation. Link to authoritative existing documents from `design_doc.md`.
- Do not place tests, tools, dependency manifests, source code, or user-facing documentation under `.init_repo/`.
- Create detailed stage plans and stage reports only according to the lifecycle in the document contract.

### 7. Verify and hand off

Re-read every created or changed file and verify:

- no confirmed decision is missing or contradicted;
- no placeholder or interview note remains;
- existing content was preserved;
- `AGENTS.md` contains behavior rules, while technical choices and rationale live only in `design_doc.md`;
- the selected sharing or local-exclusion behavior is effective;
- no environment, dependency, or project asset was changed unintentionally.

Report the files changed, the selected visibility mode, and the first confirmed delivery stage. State clearly that implementation has not started.
