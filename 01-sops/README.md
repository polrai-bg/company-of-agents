# 01-sops/

Standard operating procedures that cross agent lanes.

## What an SOP is

A convention that more than one agent has to follow the same way, and that no single agent owns. Where deliverables land, how tasks get tracked, how work gets reviewed, when two specialists may run at once, and what makes an automation real rather than aspirational.

If a rule only affects one role, it does not belong here. It belongs in that role's `06-agents/<slug>/AGENT.md`.

## Source of truth

The files in this folder are the source of truth for cross-agent conventions. When an `AGENT.md` and an SOP disagree, the SOP wins, with one exception.

**An `AGENT.md` may override an SOP locally, but only with an explicit `### Overrides` subsection** that names the SOP, states what changes, and says why. Silence is not an override. An agent doc that says nothing about deliverables gets the SOP behavior as written.

An override looks like this:

```
## Deliverables

Follow `01-sops/deliverables.md` unless overridden below.

### Overrides

Code changes ship in the relevant code repository, not in `00-deliverables/`.
Briefs and scoping docs still default to `00-deliverables/` per the SOP.
```

## The SOPs

| File | Covers |
|---|---|
| `deliverables.md` | Where agent output lands, naming, templates, the `00-deliverables/` vs `.deliverables/` distinction |
| `task-tracking.md` | `00-tasks.md` schema, when to write a row, the single-writer rule for concurrent agents |
| `review.md` | The adversarial review contract: Validator, Skeptic, Voice Reviewer, triggers, FAIL handling |
| `parallel-work.md` | When more than one delivery specialist may run at the same time, and when the work is single-threaded |
| `automations.md` | Automation honesty: the required runner declaration and the run ledger |

## Adding an SOP

Write one when a convention has already failed at least once in real use, and when the failure crossed more than one agent. Every SOP in this folder should be traceable to a specific thing that went wrong. An SOP written in advance of the problem is a guess, and guesses accumulate into ceremony nobody follows.

Keep them short. An SOP that nobody finishes reading is not enforced.
