---
name: project-context-lite
description: Maintain lightweight context, decisions, plans, and benchmark notes for personal software projects without imposing full CI or review workflows.
metadata:
  short-description: Lightweight project context and planning
---

# Project Context Lite

Use this skill when working on a personal project that needs persistent context across sessions. The goal is to preserve the project's purpose, current state, decisions, and evidence without turning ordinary development into a heavyweight process.

## Default behavior

- Read only the context files relevant to the current task.
- Inspect the repository selectively; do not rescan the whole repository on every turn.
- Keep one active technical direction unless the user explicitly changes scope.
- Before proposing implementation, identify the problem, expected evidence, and stopping condition.
- Prefer a small, reversible change over a broad refactor.
- Record only decisions, milestones, blockers, and measured results. Do not log every command or conversation.

## Context files

Use `.agent/` in the project root when persistent project memory is needed:

- `CONTEXT.md`: stable project background, goals, constraints, and non-goals.
- `STATE.md`: current status, next action, blockers, and recent verified facts.
- `PLAN.md`: the current phase only; remove or archive stale tasks.
- `DECISIONS.md`: decisions that affect architecture, scope, or experiments.
- `BENCHMARKS.md`: reproducible performance experiments and results.
- `TODO.md`: short, actionable items that fit the current phase.

Create only the files that are useful. A small project may need only `CONTEXT.md` and `STATE.md`.

## Validation policy

Validation is proportional to risk and stage:

1. Ordinary edit: run the smallest relevant check, or no check when the change is documentation-only.
2. Local milestone: run the targeted build, smoke test, benchmark, or regression test for the changed behavior.
3. Release, merge, or resume-worthy milestone: perform a broader review once and record the result.

Do not automatically run the full test suite after every edit or commit. Do not require coverage-driven tests for their own sake. Add tests when they protect a fixed bug, behavior contract, numerical property, or high-risk boundary.

## Git and external actions

- Never commit, push, publish, or delete branches without explicit user intent for that action.
- Do not rewrite unrelated files or normalize the repository as a side effect.
- Before a commit, summarize changed files and the checks actually run; do not invent checks.

## Response format

For a new task, briefly state:

1. the relevant project context;
2. the single direction being pursued;
3. the smallest next action;
4. the validation or evidence required.

When a direction is not supported by evidence, label it as a hypothesis and measure before optimizing. When a direction is out of scope, record it as a non-goal instead of expanding the plan.
