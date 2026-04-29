# .deliverables/

Active working documents — drafts, outlines, copy, decks, ready-to-ship artifacts.

## What goes here

Marketing copy, landing page outlines, investor updates, press releases, sales collateral, any artifact intended to be read or shipped.

## What does NOT go here

- Audit handoffs / decision history → `04-memory/`
- Skill content → `03-skills/<skill>/SKILL.md` or agent-local
- Agent specs → `06-agents/<agent>/AGENT.md`

## Convention

- One file per deliverable. Date-prefixed: `YYYY-MM-DD-<topic>.md`.
- For multi-part deliverables, use a folder: `2026-04-28-launch/post.md`, `landing.md`, `email.md`.
- Add YAML frontmatter (`type`, `author`, `status`, `audience`, `related-audits`).

## Why dot-prefixed

`.deliverables/` is hidden from default `ls`. These are outputs, not framework structure.
