# Company of Agents

> Stop chatting with AI. Run a company of them.

A tool-agnostic framework for ops teams that need AI to do real work — not just answer questions. Plain markdown files, an org chart, a Chief of Staff at the front who routes every request to the right specialist. Open-sourced by [POLR AI](https://www.polrai.com).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Made with Markdown](https://img.shields.io/badge/made_with-markdown-blue.svg)](https://www.markdownguide.org/)
[![Tool Agnostic](https://img.shields.io/badge/tool-agnostic-green.svg)]()

---

## The problem

You paste the same context into every conversation.
You ask one chatbot to do five jobs and it does none of them well.
You can't tell what it remembered, what it forgot, or where the rules even live.

## The fix

A **Company of Agents** is a structured org chart of specialized AI agents — each with a defined role, scope, and skills — coordinating through a single Chief of Staff agent that routes every incoming request to the right specialist. The whole system is plain markdown files in 6 folders.

Setup is one command and a 30-minute interview. At the end you have a complete operating system for your work.

## Quick start

**Requirements:** any AI agent tool that can read files and follow markdown — Claude Code, Cursor, GitHub Copilot, Windsurf, Codex, Gemini CLI, OpenClaw, etc.

```bash
# 1. Clone or copy the template
git clone https://github.com/<owner>/company-of-agents.git my-company
cd my-company

# 2. Open the folder in your AI tool
# 3. Say:
"Run bootstrap-company"
```

That's it. The bootstrap interview takes over.

## What's in the template

```
my-company/
├── AGENTS.md                                 ← entry point, points at the skill
└── 03-skills/bootstrap-company/SKILL.md      ← the interview that builds your OS
```

Two files. The skill builds out the rest of the framework based on your answers.

## What you get after running bootstrap

```
my-company/
├── AGENTS.md
├── 01-identity/      who the company is, who you are, principles
├── 02-context/       what the company knows: domain, projects, status
├── 03-skills/        shared workflows
├── 04-memory/        what persists across sessions
├── 05-connections/   how agents reach real systems (Gmail, CRM, etc.)
├── 06-agents/        the roster — Chief of Staff + every specialist
└── .deliverables/    drafts, copy, outlines, ready-to-ship artifacts
```

## How it works

```
Your request
     │
     ▼
Chief of Staff  ◄── reads identity + context
     │
     ├─ triage      what kind of work is this?
     ├─ clarify     ask one question if intent is ambiguous
     └─ route       hand off to the right specialist
            │
            ▼
       Specialist agent  ──► uses skills, connections
            │
            ▼
       Verify ──► Update memory ──► Report back
```

## The bootstrap interview — 6 phases

| Phase | What it captures |
|---|---|
| **1. Company essence** | Name, synopsis, stage, 12-month north star, principles |
| **2. The principal** | Who you are, work style, decision style, hard nos |
| **3. Domain** | Industry, vocabulary, active projects |
| **4. Team design** | Either you name the roles, or describe the work and let it propose them |
| **5. Connections** | What systems agents reach, at what permission level |
| **6. Automations** | Recurring work + which agent owns it |

One question per turn. Pause and resume across sessions. Nothing gets written until you confirm.

## Tool-agnostic

Plain markdown. Runs anywhere. Switch tools tomorrow and the OS comes with you.

| Tool | Shim file (1 line, points at AGENTS.md) |
|---|---|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursor/rules/main.mdc` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Windsurf | `.windsurfrules` |
| Gemini CLI | `GEMINI.md` |

## Use cases

- **AEC ops teams** — Submittals, RFIs, preconstruction, subcontractor compliance — agents your team can actually trust
- **Founders** — Your full org as agents you can talk to before you can afford to hire
- **Operators inside a company** — Your role's playbook, encoded

## DIY or DFY

The framework is free and open-source — fork it, run it, modify it.

If you want it implemented in your workflows for you, [POLR AI](https://www.polrai.com) builds Company-of-Agents systems for AEC ops teams. We handle discovery, build the agents around your real processes, integrate with the tools you already use (Procore, Bluebeam, spreadsheets), and train your team.

Typical engagement: 4–6 weeks to first working system. Fixed-fee.

📩 **bg@polrai.com** · 📅 [Book a 30-minute call](https://www.polrai.com)

## Safety defaults

- External actions (sending emails, posting publicly, spending money, deleting data) require explicit confirmation
- Plain markdown — no lock-in, no vendor, no SaaS to cancel
- Fork, edit, modify — the framework is yours

## FAQ

**Does this work with my AI tool?**
Yes if it can read files and follow markdown. Most can. The OS is plain text.

**Do I need engineering to run this?**
No. The whole system is markdown + an interview. The only command is `git clone`.

**What does the framework cost?**
Zero. It's a folder of text files.

**What does POLR AI's implementation cost?**
Depends on scope. Most engagements are fixed-fee, 4–6 weeks. [Book a call](https://www.polrai.com) for a quote.

**Can I edit it by hand?**
Yes — that's the point. It's not an app, it's your files.

**What if I want to switch AI tools later?**
Add a one-line shim (see Tool-agnostic above) and you're done. No migration, no export.

## License

[MIT](LICENSE). Use it, fork it, ship it.

## Built by

[POLR AI](https://www.polrai.com) — making AI useful where work actually happens.

We use this framework as the spine of every implementation we do for AEC ops teams. Open-sourced so you can see how we think.

---

*30 minutes to know if it's for you. 4 weeks to have it running in production.*
