# Agent rules for this repository

This file is the single source of truth for every AI agent working here.
Codex reads it directly. Claude Code reads it through `CLAUDE.md`, which imports this file.
Change the rules here only; never copy them into another file.

## Project

<!-- TODO: fill in once the project is defined -->
- What it is:
- Who it is for:
- Stack and language:
- How to install, run and test:

## Shared context

Read these before starting any task:

- `docs/SPEC.md`: what is being built and why
- `docs/TASKS.md`: the task list and who owns each task

If a task is not in `docs/TASKS.md`, add it there before working on it.

## Roles

| Step | Owner | Output |
|------|-------|--------|
| Plan | Claude | Spec section in `docs/SPEC.md`, tasks in `docs/TASKS.md` |
| Build | Codex | Code and tests on a feature branch, pull request |
| Review | Claude | Review notes on the pull request |
| Ship | Human | Merge to `main` |

The split is a default, not a restriction. Either agent may do any step when the human asks.

## Workflow

1. One task, one branch, one pull request.
2. Branch names: `feat/<short-name>`, `fix/<short-name>`, `docs/<short-name>`.
3. Never commit directly to `main`. Never merge a pull request; only the human merges.
4. Before opening a pull request: run the tests and say in the description what was run and what the result was.
5. The pull request description states the task it closes, what changed, and anything left undone.
6. When a task is finished, mark it done in `docs/TASKS.md` in the same pull request.

## Handoff between agents

Agents do not talk to each other directly. They hand off through the repository:

- The planner writes the spec and tasks; the builder reads them.
- The builder opens a pull request; the reviewer comments on it.
- Review notes that need a code change become new commits on the same branch.
- Open questions for the human go in the pull request description under "Questions".

## Coding rules

<!-- TODO: fill in once the stack is chosen: formatter, linter, test framework, naming -->
- Keep changes small and limited to the task.
- Do not add a dependency without stating why in the pull request.
- Never commit secrets, tokens or `.env` files.
