# .deliverables/ (local scratch only)

**This is not the deliverables folder.** Shipped work goes to `00-deliverables/`.

See `01-sops/deliverables.md` for the rule.

## What this folder is

Local-only working scratch. Everything here except this README is gitignored. Nothing in this folder is part of the repo, travels to another machine, or survives a fresh clone.

## Why it still exists

Earlier versions of this framework shipped deliverables here, on the theory that outputs are not framework structure and should stay hidden.

That was wrong. Gitignored work is not tracked, not reviewable, and not linkable from `00-tasks.md`, which means a reviewer cannot check it and the task index points at nothing. The convention moved to `00-deliverables/`, tracked. The folder stays only so that the old name has a sign on it.

## Rules for agents

- **Never ship a deliverable here.** Use `00-deliverables/YYYY-MM-DD-<slug>/`.
- **Never link to a path in here from `00-tasks.md`, from `04-memory/`, or from any other tracked file.** The link will be dead for everyone but this machine.
- If you find a `.deliverables/` path referenced somewhere, treat it as a broken historical reference, not as an instruction.
- Use this folder only for genuine throwaway scratch that must not be committed. If you are unsure, use `00-deliverables/`.
