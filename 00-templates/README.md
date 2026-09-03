# 00-templates/

Reusable formats that get filled in rather than rewritten. Proposals, client briefs, decision docs, recurring report shapes, anything with a structure worth keeping stable across instances.

`01-sops/deliverables.md` tells every agent to look here first before inventing a format. This folder is what makes that instruction resolve.

## What belongs here

A template earns a spot when the same structure has been rebuilt from memory twice. Before that, it is premature. After that, it is drift.

## Convention

- One folder per template: `00-templates/<template-name>/`.
- The template file itself is `TEMPLATE.md`, with placeholders written so an agent can tell what to replace.
- Supporting assets (a rendered PDF, a styled HTML version, an example fill) live alongside it in the same folder.

```
00-templates/
└── proposal/
    ├── TEMPLATE.md
    └── example-filled.md
```

## What does not belong here

- A finished, filled-in artifact. That is a deliverable, and it goes to `00-deliverables/YYYY-MM-DD-<slug>/`.
- A workflow (how to do the work). That is a skill, and it goes to `03-skills/` or under the owning agent.

This folder ships empty. Populate it from real work.
