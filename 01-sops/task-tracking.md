# SOP: Task Tracking

## Source of truth

Every active task across all agents is tracked in `00-tasks.md` at the repo root. One table, one file, company-wide.

## Schema

| Field | Description |
|---|---|
| id | `t-YYYY-MM-DD-NNN`, where NNN is a 3-digit sequence within that date |
| owner | The agent responsible (Chief of Staff, CMO, CTO, or whatever the roster calls it) |
| task | One-line description of the work |
| status | `open` / `in_progress` / `blocked` / `done` / `abandoned` |
| started | Date the agent began work |
| updated | Date of the last status change |
| deliverable | Path to the folder under `00-deliverables/`, or a short note for non-file output |

## Status values

- `open`: identified, not yet started.
- `in_progress`: actively being worked.
- `blocked`: waiting on an external dependency. Name the blocker in the task description.
- `done`: finished, deliverable linked.
- `abandoned`: explicitly dropped, with the reason in the task description.

## When to write

Two tiers, by size of the work.

- **Small, same-session work** (one draft, one read-out, one answer produced in a single sitting): write the row once, at completion, status `done`, with the deliverable link. No live status maintenance. This is the common case. Do not let ceremony block shipping.
- **Multi-session or blocked work** (a build, a piece waiting on approval, anything you will put down and pick back up): open the row when you start, status `in_progress`, and update `updated` on every status change.

Orchestration steps are not tasks. Triage, clarification, routing, and the daily digest do not get rows. The decision log and `04-memory/` cover those.

## Single-writer rule when agents run concurrently

`00-tasks.md` is a single shared file. When several agents run at the same time, concurrent edits to it overwrite each other and the company task list silently loses rows. Nobody notices, because the file still looks fine.

So under agent teams the rule inverts:

- **Teammates do not write to `00-tasks.md`. At all.** Not to open a row, not to update one, not to close one.
- **Each teammate writes only inside its own deliverable folder** (`00-deliverables/YYYY-MM-DD-<slug>/`). Reviewers write only their own `REVIEW-*.md`, per `01-sops/review.md`. One writer per file, always.
- **Each teammate reports task state in its final message**: what it did, the deliverable path, the status it believes the task is in, and anything unresolved.
- **The lead session reconciles `00-tasks.md` at the end**, in one pass, from those reports. One writer, one pass, no collisions.

The deliverable folder is the durable record. `00-tasks.md` is the index the lead maintains over it. If the two ever disagree, the deliverable folder is what actually happened.

## Enforcement

The mechanism is a verification checklist. Every deliverable-producing skill ends with a "task row written or updated" item, and the work is not done until that item passes. With no checklist anywhere, the table ends up empty.

Do not over-trust it. A checklist only fires when the skill carrying it is invoked, and invoking the skill is itself something someone has to remember. Enforcement relocates the memory dependency; it does not remove it. Expect partial coverage on ad-hoc work, and expect the lead to reconcile the gap.

So measure rather than assume. After roughly a month of real use, count deliverable folders shipped against rows written. Harden the SOP if the rows are earning their friction, lighten it if they are not, and decide on that count rather than on faith in the mechanism. Writing the row automatically is the only version that does not depend on someone remembering at all.

## Disruption recovery

If an agent crashes or a session dies mid-task, the orphaned `in_progress` row is the recovery signal. This is the reason multi-session work tracks live status even though small work logs only at completion: a row that says `in_progress` with a stale `updated` date is the only artifact that says "someone started this and never came back."

Whoever picks the work back up confirms the task with the lead before resuming, rather than assuming the previous agent's plan.

## Filtering

Agents filter by `owner` to find their own work. The principal reads the whole list as the company-wide pane of glass.
