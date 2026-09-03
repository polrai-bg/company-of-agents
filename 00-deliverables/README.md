# 00-deliverables/

**This is the deliverables folder.** Every artifact an agent produces ships here. The `00-` prefix sorts it to the top of the directory listing so it is the first thing anyone sees.

It is tracked in git on purpose. Deliverables have to be reviewable, linkable from `00-tasks.md`, and present in a fresh clone. Work that only exists on one machine is work nobody can check.

The full convention lives in `01-sops/deliverables.md`. The short version:

## Convention

- One folder per deliverable: `YYYY-MM-DD-<slug>/`, using the creation date.
- Inside it, a primary file (`BRIEF.md`, `STRATEGY.md`, `POST.md`, `DECISION.md`, or whatever fits) plus any supporting assets.
- Reviewer files land here too: `REVIEW-validator.md`, `REVIEW-skeptic.md`, `REVIEW-voice.md`. See `01-sops/review.md`.
- Check `00-templates/` before writing a format from scratch.

```
00-deliverables/
└── 2026-03-11-renewal-pricing-options/
    ├── DECISION.md
    ├── REVIEW-validator.md
    ├── REVIEW-skeptic.md
    └── comparison.csv
```

## What does NOT go here

| Content | Where it goes |
|---|---|
| Decision history, audit trail, digests | `04-memory/` |
| Shared workflows | `03-skills/<skill>/SKILL.md` |
| Agent-local workflows | `06-agents/<agent>/skills/<skill>/SKILL.md` |
| Agent specs | `06-agents/<agent>/AGENT.md` |
| Reusable formats | `00-templates/` |
| Throwaway scratch | `.deliverables/` (gitignored, never ship there) |
