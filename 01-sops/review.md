# SOP: Adversarial Review

Cross-agent convention for how a deliverable gets checked before it reaches the principal.

## Why this exists

Most agent frameworks ask every agent to verify its own work, and some ask every agent to challenge the principal's requests. Both of those point inward. Neither covers one agent checking *another* agent's output.

Self-verification is self-graded. An agent that got a number wrong will also check it wrong, because it will check it against the same misreading that produced it. The gap does not close by asking the agent to try harder. It closes by putting a different agent, with a different job, in front of the output.

Three reviewers close that gap:

| Reviewer | Its one question | Authority |
|---|---|---|
| **Validator** | Is this **true**? | Can return FAIL. A FAIL means the task is not done. |
| **Skeptic** | Is this **sound**? | Advisory only. Never blocks. |
| **Voice Reviewer** | Would the principal **say this out loud** to a peer? | Can return FAIL. Voice only. A FAIL means not shippable as voice. |

All three are **output-facing**. They review deliverables produced by other agents. They do not take requests from the principal and they do not challenge the principal's asks. Every agent already does that.

Validator and Skeptic are scaffolded by default in every company. The Voice Reviewer exists only when the company produces public copy meant to sound like the principal personally, and it is offered during bootstrap rather than assumed.

## Scope of each reviewer

**Validator.** Numbers tie to source. Claims trace to something checkable. File paths, branches, and URLs resolve. Arithmetic holds. Dates are real. Names are spelled the way the source spells them.

**Skeptic.** Assumptions, failure modes, second-order effects, strategic fit. What breaks if the main assumption is wrong. What this commits the company to that nobody priced in.

**Voice Reviewer.** Voice only. Runs on public copy, outbound email, and web copy meant to sound like the principal. Does not run on invoices, scopes, internal punch lists, or anything the principal would never personally say. On a FAIL, it may attach an advisory rewrite of a few lines inside its own file. It never edits the draft.

## When review is required

Review fires when a deliverable contains **any** of these five:

| Trigger | Examples |
|---|---|
| **A number** | Financial reads, invoices, estimates, pricing, any metric that appears in copy |
| **A named client** | Any real customer or prospect named in the artifact |
| **A public claim** | Case studies, social posts, website copy, newsletters, speaking material |
| **An external send** | Anything the Chief of Staff would actually send: emails, posts, invoices, proposals |
| **A strategy shift** | Positioning changes, ideal-customer changes, a new offering, anything that amends the plan |

## When review is skipped

- Internal scratch and working notes.
- Routing decisions and triage.
- Daily briefs and digests. These summarize state that already exists somewhere. They do not assert new claims.
- Early drafts explicitly marked as such, before the specialist considers them ready.

If in doubt, run the review. The cost of a skipped review on a client-facing number is much higher than the cost of an unnecessary one.

## Flow

```
specialist drafts -> 00-deliverables/YYYY-MM-DD-<slug>/
  |
  +- validator       -> REVIEW-validator.md   (PASS or FAIL)
  |     FAIL -> back to the specialist to fix
  |
  +- skeptic         -> REVIEW-skeptic.md     (objections, or "no material objection")
  |
  +- voice reviewer  -> REVIEW-voice.md       (PASS or FAIL; only when the piece
  |                                            is meant to sound like the principal)
  |     FAIL -> not shippable as voice; specialist rewrites
  |
  +- Chief of Staff frames the decision for the principal, attaching skeptic findings
```

The reviewers can run in any order, or all at once. The Skeptic does not wait for a Validator PASS, because a factual error and a reasoning flaw are independent problems and fixing one does not surface the other.

## One file per reviewer

Each reviewer writes exactly one file, inside the deliverable folder:

- `REVIEW-validator.md`
- `REVIEW-skeptic.md`
- `REVIEW-voice.md`

**Reviewers never edit the deliverable, and never edit each other's review files.** This is a hard rule with two jobs. It keeps the specialist as the only author of the work, so review does not quietly become co-writing. And it means reviewers running at the same time cannot overwrite each other, which is what makes review concurrency safe. See `01-sops/parallel-work.md`.

## Re-validation cap

A Validator FAIL goes back to the specialist, who fixes and resubmits. A Voice Reviewer FAIL goes back the same way: the piece is not shippable as voice, and the specialist rewrites.

**Maximum two re-validations, and two re-reviews.** If the deliverable still fails on the third pass, stop. Escalate to the principal with all three reports attached and a plain statement of what is still unresolved.

Two reasons for the cap. An unbounded fix-and-recheck loop burns time and tokens with nobody watching it. And a third consecutive failure usually means the task was mis-scoped rather than mis-executed, which is a decision for the principal, not another lap.

## What a FAIL is, and is not

A Validator FAIL requires a **specific, checkable, reproducible** defect. Every FAIL names three things:

1. The exact claim in the deliverable.
2. The exact source consulted.
3. The discrepancy between them.

"The revenue figure in section 2 reads $48,000. The source file shows $42,800 for the same period. Off by $5,200" is a FAIL. "The numbers feel high" is not.

The Validator may **not** fail work for being unpersuasive, poorly written, strategically unwise, or stylistically off. Strategy is Skeptic territory, and it is advisory. Voice is Voice Reviewer territory. If the Validator finds itself writing "I think" or "this feels", it has left its lane and the finding should be dropped or handed to the right reviewer.

## Anti-theater rule

**"No material objection" is a valid and expected outcome.** So is a clean Validator PASS with zero findings. So is a clean Voice PASS.

A reviewer that always finds something is manufacturing findings to justify its own existence, and it trains everyone downstream to skim review files instead of reading them. Performed doubt is as useless as reflexive agreement.

Reviewers are measured on the objections the principal actually acts on, not on the volume they produce.

## Task tracking

Review is part of the specialist's task, not a separate task. The specialist's row in `00-tasks.md` stays `in_progress` until review clears. Do not open a new task row for a review, and do not mark a deliverable `done` while a FAIL is outstanding.
