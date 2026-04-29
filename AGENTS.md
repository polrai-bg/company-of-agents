# New Company — Bootstrap Required

This folder is a fresh, empty Agentic OS. To turn it into a real company, run the **`bootstrap-company`** skill at `03-skills/bootstrap-company/SKILL.md`.

That skill will interview the principal in phases (identity → principal → domain → team → connections → automations) and scaffold the entire OS — `01-identity/`, `02-context/`, `04-memory/`, `05-connections/`, `06-agents/` — based on the answers.

## Trigger

Any of these prompts will run it:
- "Run `bootstrap-company`"
- "Set up this company"
- "Initialize this Agentic OS"

## What you get after running

A complete OS with this shape:

```
01-identity/      who the company is, who the principal is, operating principles
02-context/       what the company knows: domain, projects, current state
03-skills/        shared workflows (starts with add-new-agent for incremental growth)
04-memory/        cross-session persistence
05-connections/   one file per external system
06-agents/        the roster — each agent has AGENT.md, skills/, memory/, optionally automations/
AGENTS.md         updated entry point pointing at the populated OS
```

Verification = required section in every `SKILL.md` and `AGENT.md`.
Automations = under the agent that owns them.

## Tool-agnostic

This OS is plain markdown and travels across tools. If you adopt a specific agentic tool, create a one-line shim file (`CLAUDE.md`, `.cursor/rules/main.mdc`, `.github/copilot-instructions.md`, `GEMINI.md`, `.windsurfrules`) containing only:

> See AGENTS.md — single source of truth for this Agentic OS.

Never duplicate content from this OS into a tool-specific file. Single source of truth or bust.
