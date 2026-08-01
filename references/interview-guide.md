# Initialization Interview

Use this guide adaptively. Populate facts from the target project first, then ask only about unresolved decisions or contradictions.

## Question discipline

- Ask exactly one decision per turn.
- State the evidence or dependency that makes the decision necessary.
- Give a recommended answer and explain the practical tradeoff.
- Wait for the user's answer before following the next branch.
- Never ask the user for a fact that can be found with read-only inspection.
- Do not write scratch documents into the target project during the interview.

When the user supplies several decisions in one answer, accept all unambiguous decisions, identify any conflict, and continue with the next unresolved dependency.

## Required decision areas

Cover each area, but skip questions already resolved by the request or repository:

1. **Objective and success**: project outcome and measurable completion criteria.
2. **Users and scenarios**: intended users and the core situations the project must support.
3. **Scope**: current delivery boundary and explicit non-goals.
4. **Current state**: existing capabilities, constraints, known problems, and authoritative documents.
5. **Technical plan**: stack, architecture boundaries, key integrations, and reasons for choices.
6. **Runtime plan**: runtime versions, environment creation and activation commands, package manager, and dependency entry points.
7. **Project assets**: source, tests, tools, dependency manifests, and user-facing documentation in their normal project locations.
8. **Working conventions**: durable rules that future Agents must follow.
9. **Validation**: test strategy, acceptance evidence, and completion rules.
10. **Delivery stages**: dependency-ordered, independently acceptable increments.
11. **Initialization visibility**: shared through version control or private to the local worktree.

Do not select a framework, database, package manager, deployment target, or other consequential technology merely to fill a blank. Recommend an option based on discovered constraints and let the user decide.

## Stage proposal

Present the full recommended sequence before confirming individual stages. For each stage include:

- objective;
- included scope;
- non-goals;
- prerequisites and dependencies;
- primary deliverables;
- acceptance criteria;
- known risks;
- whether it can proceed in parallel with another stage.

Keep future stages at roadmap depth. Defer task-level detail until a stage is about to start.

## Final confirmation

Before writing, provide one consolidated summary and an exact write set. Separate:

- facts discovered from the repository;
- user-confirmed decisions;
- Agent recommendations the user accepted;
- unresolved conflicts;
- proposed additions to an existing `AGENTS.md`.

Do not treat silence or a partial answer as approval to write.
