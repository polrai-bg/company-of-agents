# SOP: Parallel Specialist Work

Cross-agent convention for when more than one delivery specialist may run at the same time.

## Why this exists

Orchestrator-worker concurrency pays off when the workers explore independent territory and the lead's job is to combine findings nobody else touched. It breaks down when the workers form competing judgments about the same shared facts. At that point the "synthesis" step stops being a merge and becomes an argument, and simultaneous writes into shared state produce conflicts that nobody was assigned to resolve.

`01-sops/review.md` already gets this right for the review layer. Validator, Skeptic, and Voice Reviewer run concurrently because each is read-only against the deliverable, each writes only its own file, and none of them asserts a conclusion into another's output. **That is the pattern to copy.** This SOP extends the same discipline to the delivery agents.

## The rule

**Two or more delivery specialists may run in parallel only when both of these hold:**

1. They read **disjoint sources**. Not the same section of live state, interpreted two ways.
2. They write **disjoint files**. Never two specialists drafting into the same deliverable or the same decision.

If either fails, the work is single-threaded. Route one specialist at a time through the Chief of Staff, sequentially, and let the Chief of Staff (or the principal) do the adjudication that a shared-state decision actually requires.

## Good fan-out

One specialist investigates a vendor API constraint that will shape the build. Another independently researches competitor positioning for the same engagement.

Disjoint sources (an API specification versus public competitor material). Disjoint output files. Nothing to reconcile at the end except stapling two independent findings together. Both threads produce facts the lead did not have, and neither thread's answer changes the other's.

## Bad fan-out

Three specialists spawned at once to weigh in on the same pricing decision. All three read the same plan and the same client history, and all three return a judgment about it.

There is no clean merge here, because **the disagreement between them is the decision**. And it just got made by whichever output the lead happened to read first, rather than by the Chief of Staff, deliberately, with all the inputs on the table. The parallelism did not speed the decision up. It hid who made it.

## Test before spawning more than one specialist at once

- [ ] Do they need different sources, or the same source read twice?
- [ ] Are they producing independent facts, or competing opinions about one thing?
- [ ] Do they write to different files?

Any answer of "same source", "competing opinions", or "same file" means do not fan out. One specialist, then the Chief of Staff frames the decision, the same as every other routing call.

## Cost note

Parallel multi-agent work runs meaningfully more tokens than a single session, because each agent carries its own context window and each one re-reads the shared context from scratch.

That cost is worth paying for research-shaped work that genuinely decomposes into independent threads. It is not worth paying to have three specialists form redundant opinions about one fact base that the Chief of Staff could have read once.
