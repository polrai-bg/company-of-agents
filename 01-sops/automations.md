# SOP: Automations

## The problem this solves

**A cron expression in a markdown file does not run itself.**

It is easy to write `0 7 * * 1-5` into an automation file, describe the output, and then quietly believe the automation exists. It does not. Nothing is scheduling it. Nothing fires it. The file is a checklist that reads like a robot.

This matters more than it sounds, because the failure is silent and it compounds. The principal assumes the Monday brief ran. The agent assumes the principal saw it. Nobody looks. Weeks pass.

Every automation must name its runner, and the OS must be able to prove that a wired automation actually fired.

## Runner declaration (required)

Every file under an agent's `automations/` folder carries a `## Runner` section stating exactly one of:

- **`manual`**: not wired to any scheduler. Runs when the principal or an agent invokes it by hand. **This is the honest default**, and it is the correct value for every automation the day it is written.
- **`scheduled: <trigger name or id>`**: fired by a named scheduled trigger in the agent tool. Name it so it can be found and audited. "There's a schedule somewhere" is not a runner declaration.
- **`workflow: <tool>/<workflow name>`**: fired by a named workflow in an external automation tool. The workflow must also appear in the matching `05-connections/<tool>.md` file.

The cron expression in the file is the **intended** schedule. It stays aspirational until a runner is declared and wired. Wiring is a build task plus an approval to turn it on, like any other external-facing change.

Automations produce drafts or signals. They never auto-send. See the hard nos in `AGENTS.md`.

## Run ledger (required once wired)

Every wired automation appends one line per run to `04-memory/automation-runs.md`:

```
| date | automation | outcome (ok / partial / failed) | output path or note |
```

If the ledger shows no runs for a wired automation across two consecutive scheduled periods, the Chief of Staff surfaces it as a broken automation. It does not silently assume the run happened and the logging failed. A missing log line and a missing run look identical from the outside, and both are worth a look.

## No live plan facts in automation files

**Automation files must not embed strategy data.** No target dates, no metric definitions, no thresholds that come from the plan, no client-specific numbers.

Point at the source instead:

> Read the current quarter target and its conditions from the plan in live state.

Not:

> Check whether revenue has cleared $180,000 before the March 14 checkpoint.

Embedded plan facts rot. The plan gets updated in one place and the automation keeps asserting the old number, with full confidence, on a schedule. An audit of a running system found automations still checking against a deadline that had already passed, which meant every run since that date had been quietly measuring the wrong thing.

Configuration that genuinely belongs to the automation (its own cadence, its own output path, its own failure mode) stays in the file. That is not plan data.

## Status table

Keep a table like this in this file, listing every automation in the company and its current runner. It is the one place to answer "what is actually running here?"

| Automation | Owner | Runner | Wired since |
|---|---|---|---|
| _(none yet)_ | | | |

Update this table and the automation's own `## Runner` section together. Two places, one change, always in the same commit. If they disagree, the automation file wins and this table is stale.

## Verification

- [ ] Every file in every `automations/` folder has a `## Runner` section.
- [ ] No automation file embeds plan facts (targets, deadlines, metric definitions, thresholds).
- [ ] Every wired automation logs to `04-memory/automation-runs.md`.
- [ ] The status table above matches the per-file runner declarations.
- [ ] No automation sends anything externally without routing through the approval path.
