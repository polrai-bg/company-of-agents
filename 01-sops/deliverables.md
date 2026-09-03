# SOP: Deliverables

## Default destination

All agent deliverables ship to `00-deliverables/YYYY-MM-DD-<slug>/` at the repo root.

- `YYYY-MM-DD` is the date the deliverable was created.
- `<slug>` is a short kebab-case description (for example `q3-pricing-review`, `launch-week-copy`).
- Each deliverable folder holds a primary file (`BRIEF.md`, `STRATEGY.md`, `POST.md`, `DECISION.md`, or similar) plus any supporting assets.
- Review files land in the same folder. See `01-sops/review.md`.

## Do not confuse `00-deliverables/` with `.deliverables/`

Two folders have similar names. Only one is correct.

| Folder | Status | Use it for |
|---|---|---|
| `00-deliverables/` | Tracked in git. **The default for all agent work.** | Every draft, brief, strategy, post, case study, scoping note, decision doc, and reviewer file. |
| `.deliverables/` | Gitignored local scratch. Not part of the repo. | Throwaway scratch only. Never ship here. |

Work that lands in `.deliverables/` is invisible to everyone but the machine that wrote it. It cannot be reviewed, cannot be linked from `00-tasks.md`, and does not survive a fresh clone. **Never create a new link to a `.deliverables/` path from any tracked file.** See `.deliverables/README.md`.

## Using templates

When a deliverable has an established format (a proposal, a client brief, a decision doc), check `00-templates/` first before writing from scratch.

1. List `00-templates/` and look for a folder matching the format you need. Each template folder holds a `TEMPLATE.md`.
2. Copy it and fill in the specifics for the current task.
3. Save the finished deliverable in its dated folder under `00-deliverables/`.

If a format gets rebuilt from memory twice, it belongs in `00-templates/`.

## When this rule applies

Any draft, brief, strategy, post, case study, scoping note, decision doc, or other artifact that ships as a file.

## When to override

Some roles produce output that does not ship as a file in this repo. Their `AGENT.md` states the override explicitly in an `### Overrides` subsection. Two common ones:

- A technical role: code changes ship in the relevant code repository. Briefs and scoping docs still go to `00-deliverables/`.
- The Chief of Staff: approved sends go out through the relevant channel. The draft still lands in `00-deliverables/` first.

**If an `AGENT.md` does not state an override, the default in this SOP applies.** See `01-sops/README.md` for the override mechanism.

## Naming hygiene

- Use the creation date, not the planned publish date. A post drafted today and published next Tuesday is dated today.
- Make the slug specific enough that someone scanning the folder list can guess what is inside. `2026-03-11-notes` fails this. `2026-03-11-renewal-pricing-options` passes.
- One folder per deliverable. Do not pile unrelated drafts into one dated folder.

## Writing conventions

Every deliverable follows the writing conventions the principal set in `01-identity/USER.md`, plus the vocabulary rules in `02-context/vocabulary.md`. Both are captured during bootstrap.

Conventions apply to the deliverable body, its frontmatter, its file names, and its supporting files alike. A convention like "never use em-dashes" or "always spell out the client's legal name on first use" is not a prose-only rule, and a reviewer will check the whole artifact.

Generic filler is a defect, not a style preference. Phrases like "optimize your workflow", "synergies", or "leverage AI to drive value" are a tell that the agent is writing around a gap in its context instead of naming the gap. Do not ship them.

## Linking back

Every deliverable links to its task row in `00-tasks.md`. See `01-sops/task-tracking.md` for who writes that row and when. Small same-session deliverables may write the row at completion, and teammates running under a lead do not write it at all.
