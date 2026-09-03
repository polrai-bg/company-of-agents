# Company of Agents

> Stop chatting with AI. Run a company of them.

A tool-agnostic framework for ops teams that need AI to do real work, not just answer questions. Plain markdown files, an org chart, a Chief of Staff at the front who routes every request to the right specialist, and a review layer that can fail work before you ever see it. Open-sourced by [POLR AI](https://www.polrai.com).

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Made with Markdown](https://img.shields.io/badge/made_with-markdown-blue.svg)](https://www.markdownguide.org/)
[![Tool Agnostic](https://img.shields.io/badge/tool-agnostic-green.svg)]()

---

## The problem

You paste the same context into every conversation.
You ask one chatbot to do five jobs and it does none of them well.
You can't tell what it remembered, what it forgot, or where the rules even live.
And when it gets a number wrong, the only thing checking it is the same model that got it wrong.

## The fix

A **Company of Agents** is a structured org chart of specialized AI agents, each with a defined role, scope, and skills, coordinating through a single Chief of Staff agent that routes every incoming request to the right specialist.

The whole system is plain markdown: nine numbered folders and a task list at the root. Deliverables land in dated folders. Cross-agent conventions live in `01-sops/` so no single agent owns them. And output that carries a number, a client name, a public claim, an external send, or a strategy change goes through a reviewer before it reaches you.

Setup is one command and a 30-minute interview. At the end you have a complete operating system for your work.

## Quick start

**Requirements:** any AI agent tool that can read files and follow markdown. Claude Code, Cursor, GitHub Copilot, Windsurf, Codex, Gemini CLI, OpenClaw, and others.

```bash
# 1. Clone or copy the template
git clone https://github.com/polrai-bg/company-of-agents.git my-company
cd my-company

# 2. Open the folder in your AI tool
# 3. Say:
"Run bootstrap-company"
```

That's it. The bootstrap interview takes over.

## What's in the template

```
my-company/
├── AGENTS.md                             ← entry point, plus the framework rules
├── 00-tasks.md                           ← company task index, empty and ready
├── 00-deliverables/README.md             ← where agent output lands (tracked in git)
├── 00-templates/README.md                ← reusable formats, populate from real work
├── 01-sops/                              ← cross-agent conventions
│   ├── README.md                           what an SOP is, how to override one
│   ├── deliverables.md                     where work ships and how it's named
│   ├── task-tracking.md                    the task schema and the single-writer rule
│   ├── review.md                           the adversarial review contract
│   ├── parallel-work.md                    when two specialists may run at once
│   └── automations.md                      runner declarations and the run ledger
├── 03-skills/
│   ├── bootstrap-company/SKILL.md        ← the interview that builds your OS
│   └── add-new-agent/SKILL.md            ← add one specialist, later, on evidence
└── .deliverables/README.md               ← local scratch. NOT the deliverables folder.
```

Plus the usual repo plumbing: `README.md`, `LICENSE`, `.gitignore`.

The framework ships complete. The interview builds your company on top of it.

## What you get after running bootstrap

```
my-company/
├── AGENTS.md
├── 00-tasks.md          company-wide task list across every agent
├── 00-deliverables/     every artifact an agent produces, one dated folder each
├── 00-templates/        reusable formats: proposals, briefs, recurring reports
├── 01-identity/         who the company is, who you are, principles
├── 01-sops/             cross-agent conventions (shipped, not generated)
├── 02-context/          what the company knows: domain, vocabulary, projects
├── 03-skills/           shared workflows
├── 04-memory/           what persists across sessions
├── 05-connections/      how agents reach real systems (email, CRM, etc.)
└── 06-agents/           the roster: Chief of Staff, your specialists, the reviewers
```

Deliverables are tracked in git on purpose. Work nobody can link to is work nobody can check.

## How it works

```
Your request
     │
     ▼
Chief of Staff  ◄── reads identity + context + live state
     │
     ├─ triage      what kind of work is this?
     ├─ clarify     ask one question if intent is ambiguous
     └─ route       hand off to the right specialist
            │
            ▼
     Specialist agent  ──► uses skills, connections, templates
            │
            ▼
     Draft lands in 00-deliverables/YYYY-MM-DD-<slug>/
            │
            ▼
     Review gate  (fires on: a number, a client name, a public
     │             claim, an external send, a strategy shift)
     │
     ├─ Validator        is this true?              can FAIL
     ├─ Skeptic          is this sound?             advisory only
     └─ Voice Reviewer   would you say this?        can FAIL
            │
            │   FAIL ──► back to the specialist, max two re-checks
            ▼
     Chief of Staff frames the decision for you
            │
            ▼
     You approve  ──►  Chief of Staff executes the send
            │
            ▼
     Task row updated ──► memory updated
```

Reviewers never edit the work. They each write one file next to it. That is what makes it safe to run all three at the same time.

## The bootstrap interview: 6 phases

| Phase | What it captures |
|---|---|
| **1. Company essence** | Name, synopsis, stage, 12-month north star, principles, writing conventions |
| **2. The principal** | Who you are, work style, decision style, hard nos |
| **3. Domain** | Industry, vocabulary, active projects |
| **4. Team design** | Either you name the roles, or describe the work and let it propose them. Validator and Skeptic are scaffolded either way. A Voice Reviewer is offered if agents will write copy meant to sound like you. |
| **5. Connections** | What systems agents reach, at what permission level |
| **6. Automations** | Recurring work, which agent owns it, and what actually fires it. Default is `manual`, because a cron line in a markdown file does not run itself. |

One question per turn. Pause and resume across sessions. Nothing gets written until you confirm.

## Safety model

The defaults are set so that the expensive mistakes need a human in the loop, and the cheap ones do not.

- **The Chief of Staff is the only sender.** No specialist emails, posts, comments, or DMs. Ever.
- **A draft is not a send.** Everything that leaves the company is drafted, then waits for an explicit "send it."
- **Automations produce drafts or signals. They never auto-send.** And every automation declares what actually runs it, so nothing looks scheduled when it isn't.
- **Reviewers can fail work.** A Validator FAIL means the task is not done, no matter how confident the agent that wrote it was.
- **Money, client commitments, secrets, and destructive data actions are hard nos** for every agent, in every role, always.
- **An agent that can't reach live data says so.** It ships the work with the gap marked, not a number it made up.

## Tool-agnostic

Plain markdown. Runs anywhere. Switch tools tomorrow and the OS comes with you.

| Tool | Shim file (1 line, points at AGENTS.md) |
|---|---|
| Claude Code | `CLAUDE.md` |
| Cursor | `.cursor/rules/main.mdc` |
| GitHub Copilot | `.github/copilot-instructions.md` |
| Windsurf | `.windsurfrules` |
| Gemini CLI | `GEMINI.md` |

Never duplicate content into a shim. A second copy of the rules is a second source of truth, and it will drift.

## Use cases

- **AEC ops teams.** Submittals, RFIs, preconstruction, subcontractor compliance. Agents your team can actually trust.
- **Founders.** Your full org as agents you can talk to before you can afford to hire.
- **Operators inside a company.** Your role's playbook, encoded.

## DIY or DFY

The framework is free and open-source. Fork it, run it, modify it.

If you want it implemented in your workflows for you, [POLR AI](https://www.polrai.com) builds Company-of-Agents systems for AEC ops teams. We handle discovery, build the agents around your real processes, integrate with the tools you already use (Procore, Bluebeam, spreadsheets), and train your team.

Typical engagement: 4 to 6 weeks to first working system. Fixed-fee.

📩 **bg@polrai.com** · 📅 [Book a 30-minute call](https://www.polrai.com)

## FAQ

**Does this work with my AI tool?**
Yes if it can read files and follow markdown. Most can. The OS is plain text.

**Do I need engineering to run this?**
No. The whole system is markdown plus an interview. The only command is `git clone`.

**What does the framework cost?**
Zero. It's a folder of text files.

**What does POLR AI's implementation cost?**
Depends on scope. Most engagements are fixed-fee, 4 to 6 weeks. [Book a call](https://www.polrai.com) for a quote.

**Can I edit it by hand?**
Yes, that's the point. It's not an app, it's your files.

**Do I have to use the review layer?**
It only fires on five triggers: a number, a named client, a public claim, an external send, a strategy shift. Internal notes, routing, and daily digests skip it. And "no material objection" is an expected outcome, not a failure of the reviewer.

**What if I want to switch AI tools later?**
Add a one-line shim (see Tool-agnostic above) and you're done. No migration, no export.

## License

[MIT](LICENSE). Use it, fork it, ship it.

## Built by

[POLR AI](https://www.polrai.com), making AI useful where work actually happens.

We use this framework as the spine of every implementation we do for AEC ops teams. Open-sourced so you can see how we think.

---

*30 minutes to know if it's for you. 4 weeks to have it running in production.*
