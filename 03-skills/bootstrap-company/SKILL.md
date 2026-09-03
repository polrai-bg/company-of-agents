---
name: bootstrap-company
description: Comprehensively interview the principal in phases to build a complete Agentic OS from an empty folder: identity, context, team, connections, and automations.
when_to_use: The folder contains only the shipped framework files and a thin AGENTS.md pointing at this skill. Run it once at company creation. Do not run it on an already-populated OS; use add-new-agent for incremental roster changes.
---

# Bootstrap a Company

A staged interview that turns an empty folder into a complete Agentic OS. Treat the conversation like founding a real company: get the foundation right, then design the team, then wire the systems.

## Before you start

- **Confirm this is a fresh bootstrap.** If `01-identity/` already exists, or `06-agents/` has any agent in it, stop and ask the principal whether to (a) abort, (b) continue and overwrite, or (c) switch to `add-new-agent` for incremental additions.
- **The framework files are not a sign of a populated OS.** `01-sops/`, `00-tasks.md`, `00-deliverables/README.md`, `00-templates/README.md`, and `03-skills/add-new-agent/` ship with the template. Their presence is expected. Do not read them as a completed bootstrap, and do not overwrite them.
- **Write policy.** During Phases 1 through 6, write interview answers only to `04-memory/bootstrap-progress.md`, at each phase boundary. Do **not** write identity, context, connection, or agent files until Phase 7, after an explicit "yes". Each phase header below says what it *stages* for Phase 7.
- **Allow pause and resume.** After each phase, offer: "We can stop here and resume next session. Your answers so far are recorded in `04-memory/bootstrap-progress.md`."
- **One question per turn.** Never batch. Reflect each answer back in one line ("I heard X, right?") before advancing.
- **Offer a default when the principal hesitates.** Reaction beats authoring from scratch.

## The framework being built

Nine numbered folders plus one task file at the root:

```
00-deliverables/     every artifact an agent produces, one dated folder each (tracked; ships with template)
00-tasks.md          company-wide task list (ships with template, empty)
00-templates/        reusable formats (ships with template, empty)
01-identity/         SOUL.md (company), USER.md (principal), PRINCIPLES.md
01-sops/             cross-agent conventions (ships with template, complete)
02-context/          company.md, domain.md, projects.md, vocabulary.md
03-skills/           shared workflows (bootstrap-company, add-new-agent; both ship with template)
04-memory/           cross-session persistence
05-connections/      one file per external system
06-agents/           each agent has AGENT.md, skills/, memory/, optionally automations/
```

Bootstrap creates `01-identity/`, `02-context/`, `04-memory/`, `05-connections/`, and `06-agents/`. It also writes two things outside the numbered tree, once the principal names their tool in 5.5: the one-line tool shim, and one subagent definition per specialist so the lead session can actually spawn them. Everything else already exists and is the shipped framework.

- Verification is a required section in every `SKILL.md` and every `AGENT.md`.
- Automations live under the agent that owns them, and every one declares a runner.
- Automations produce drafts or signals. They never auto-send.

---

## Phase 1: Company essence (6 questions)

### 1.1 Name
> "What's the company called?"

### 1.2 Synopsis
> "Give me one or two sentences on what the company does and who it's for."

Reflect back. If it has more than one product or audience, ask which is primary.

### 1.3 Stage
> "Where are you today: idea, building MVP, MVP complete, paying customers, scaling?"

### 1.4 12-month north star
> "What's true 12 months from now if the year goes well? Pick the single most load-bearing metric or milestone."

### 1.5 Operating principles
> "What are 2 to 4 principles you want every agent in this company to operate by?"

If the principal is stuck, propose these four defaults inline and ask which to keep:

1. **Verify before claiming done.** No agent reports a task complete without a concrete observable.
2. **Route, don't sprawl.** The Chief of Staff routes. Specialists stay in their lane.
3. **Draft, don't send.** Anything that leaves the company is drafted for approval. The Chief of Staff is the sole sender.
4. **Challenge before agreeing.** Stress-test the request before responding. Reflexive agreement and reflexive contrarianism are both failures.

### 1.6 Writing conventions
> "Any writing conventions every agent must follow? Words or punctuation you never want to see, terms you always want spelled a specific way, formats you hate. These get enforced on every deliverable, so be specific."

Capture verbatim. These land in `01-identity/USER.md` and are enforced by `01-sops/deliverables.md`.

**Phase 1 stages for Phase 7:** `01-identity/SOUL.md`, `01-identity/PRINCIPLES.md`, top of `02-context/company.md`.

---

## Phase 2: The principal (4 questions)

### 2.1 Identity
> "Your name, role at the company, and email?"

### 2.2 How you work
> "How do you prefer to work? Async or sync, terse or verbose, options plus a recommendation or just options, batched or a steady stream, anything else."

### 2.3 Decision style
> "When agents bring you a decision, what makes one easy for you to act on? Specific examples beat principles here."

### 2.4 Hard nos
> "What should agents never do without explicit confirmation? These four are always on, so I'm confirming rather than asking: external sends of any kind (a draft is not a send, and the Chief of Staff is the only sender after you say 'send it'), money movement of any kind, actions on a major client even when routine, and destructive data actions. What would you add?"

Also confirm the secrets rule: agents never paste, copy, or relocate credentials. They point at where the credentials live.

**Phase 2 stages for Phase 7:** `01-identity/USER.md`.

---

## Phase 3: Domain (3 questions)

### 3.1 Industry and market
> "What industry or market does the company live in? Who are the buyers, what's the landscape, what's the size?"

### 3.2 Vocabulary
> "What 5 to 15 terms must every agent get exactly right? Words your buyers use, technical terms, internal jargon."

Capture the term plus a one-line definition each. Ask specifically what generic phrasing would signal that an agent is faking domain knowledge.

### 3.3 Active projects and deadlines
> "What's on the front burner right now? List active projects, deadlines, and stakeholders."

**Phase 3 stages for Phase 7:** `02-context/domain.md`, `02-context/vocabulary.md`, `02-context/projects.md`, the rest of `02-context/company.md`.

---

## Phase 4: Team design (variable length)

Goal: produce the full org chart with enough depth that the Chief of Staff can route correctly. Per-agent depth can deepen later via `add-new-agent`.

### 4.1 Org sketch
> "Two ways to do this. Option A: tell me the roles you want. Option B: describe the work that needs to happen and I'll propose a team. Which?"

### 4.2 If Option A: confirm the list
Reflect the list back. Ask: "Anything missing? Anything that should be split or merged?"

### 4.3 If Option B: propose the team
Based on synopsis, stage, domain, and active projects, propose 4 to 8 roles with a one-line role statement each. Ask for adds, drops, splits.

### 4.4 Always include the Chief of Staff
The Chief of Staff is the routing entry point and is not optional. Confirm: "I'll add a Chief of Staff as the front door. Every request lands there first and routes to specialists. OK?"

The Chief of Staff is the **lead session, never a subagent**. Do not create a subagent definition for it in the tool's subagent directory. See `AGENTS.md`.

### 4.5 Per-agent quick capture
For each agent in the confirmed list, one agent at a time:

1. **Purpose.** One sentence: why does this role exist?
2. **Top 3 responsibilities.** Three things it owns end to end.
3. **Out of scope.** What is not this role's job even though someone might assume it is. Must block external sends and money movement for every specialist.
4. **Common request shapes.** Three concrete asks in a normal week. These become routing-table rows.
5. **Escalation.** When it stops and checks. Defaults to the hard nos from 2.4.

If the principal wants more depth on one agent, offer `add-new-agent` after bootstrap.

### 4.6 The review layer (scaffolded, not interviewed)

**Validator and Skeptic are not optional and are not up for discussion.** Scaffold both. Do not ask whether the principal wants them. Do explain, in two lines, why they exist:

> "I'm also adding two review agents. The Validator checks whether a deliverable is true (numbers tie to source, claims trace, paths resolve) and can fail it. The Skeptic checks whether it's sound (assumptions, failure modes) and is advisory only. They exist because an agent that got a number wrong will also check it wrong. Self-verification is self-graded."

Then **offer** the third:

> "Will agents write public copy meant to sound like you personally? If yes, I'll add a Voice Reviewer that can fail a draft on voice alone."

Scaffold the Voice Reviewer only on a yes.

All reviewers are **output-facing**. They review other agents' deliverables. They never take requests from the principal and never challenge the principal's asks. Their contract is already written in `01-sops/review.md`, so their `AGENT.md` files point at it rather than restating it.

### 4.7 Routing table
After all agents are captured, draft the Chief of Staff routing table from the common request shapes. Show it: "These are the routing rules. Add, remove, or change?"

**Phase 4 stages for Phase 7:** `06-agents/<each-agent>/AGENT.md`, `06-agents/<each-agent>/memory/README.md`, `06-agents/README.md` (roster), `06-agents/chief-of-staff/AGENT.md` with the routing table, the review agents (`validator/`, `skeptic/`, and `voice-reviewer/` if offered and accepted), plus the Chief of Staff's five default skills: `triage-request`, `clarify-intent`, `route-to-agent`, `execute-send`, `run-daily-digest`.

---

## Phase 5: Connections (variable length)

### 5.1 What systems
> "What real systems will agents need to reach? Common ones: email, calendar, CRM, issue tracker, chat, design tool, docs or drive, payments, analytics. List the ones that matter."

### 5.2 Per system: read or write?
> "<System>: read-only, drafts only, or full read and write? And what should always require explicit confirmation before an agent acts?"

Default to the safest option. Most systems start read-only or drafts-only. External writes require confirmation per call, and the Chief of Staff is the only agent that performs an approved external send.

### 5.3 Auth
> "<System>: how is auth handled? Environment variable, OAuth, an MCP server, nothing yet? Don't paste secrets here. Just point at where they live."

### 5.4 Ownership
> "Which agent or agents primarily use <system>?"

### 5.5 Which tool runs this OS

> "Which agentic tool will you actually run this in day to day? Claude Code, Cursor, Copilot, Gemini, Windsurf, something else? I need it for two things: the one-line shim file that points the tool at `AGENTS.md`, and the directory that tool reads agent definitions from, which is where every specialist has to be registered before the Chief of Staff can spawn it."

Record two values. Do not guess either.

- **Shim path.** `CLAUDE.md` (Claude Code), `.cursor/rules/main.mdc` (Cursor), `.github/copilot-instructions.md` (Copilot), `GEMINI.md` (Gemini), `.windsurfrules` (Windsurf). One line of content, per `AGENTS.md`.
- **Subagent directory.** The directory name varies by tool. `.claude/agents/<slug>.md` is the Claude Code form. Some tools have no subagent mechanism at all.

If the tool has no way to spawn separate agents, say so plainly instead of inventing a path:

> "This tool runs one session, so the Chief of Staff will role-play the specialists from a single context. That means the Validator and the Skeptic end up reviewing work their own context wrote, which is the thing `01-sops/review.md` exists to prevent. The OS still works. The review layer is weaker than it looks, and you should know that before you lean on it."

Record that limitation in `04-memory/bootstrap-progress.md` and repeat it in the handoff.

If the principal has not picked a tool yet, write no shim and no definitions, and say in the handoff that no specialist is spawnable until the tool is named.

**Phase 5 stages for Phase 7:** `05-connections/<system>.md` for each system, each with Purpose, Mechanism, Auth, and Allowed operations. Plus the shim path and subagent directory from 5.5, which Phase 7 uses to register the roster.

---

## Phase 6: Automations (4 questions)

### 6.1 Recurring work
> "What recurring work should happen on a schedule? Examples: a weekly pipeline report, daily inbox triage, a morning brief, an end-of-day digest. List what would actually save you time."

### 6.2 Per automation
For each one, capture: intended trigger (cron or event), owning agent, output destination, and failure mode. Default failure mode is notify the principal and do not retry destructively.

### 6.3 Runner (required, do not skip)

For each automation, ask:

> "Is anything actually going to fire this on a schedule today, or is it a checklist you'll run by hand? Manual is the normal answer at bootstrap and it's the one I'll write unless you name a live scheduler."

Record exactly one runner value per automation, per `01-sops/automations.md`:

- `manual` (the default, and almost always correct on day one)
- `scheduled: <trigger name or id>`
- `workflow: <tool>/<workflow name>`

**Never produce an automation file with a cron expression and no runner.** The cron line is the intended schedule. It is aspirational until something is wired to it, and an automation that looks scheduled but is not creates a silent gap where everyone assumes it ran.

### 6.4 Confirmation gates
> "Which of these can run end to end, and which produce a draft for you to confirm before anything happens? Default is draft-only for anything externally visible."

**Phase 6 stages for Phase 7:** `06-agents/<owning-agent>/automations/<automation-name>.md` for each, every one carrying a `## Runner` section, plus the status table in `01-sops/automations.md` filled in with one row per automation.

---

## Phase 7: Confirm and scaffold

Show one summary, then ask: "Proceed? (yes / changes)". **Only write files after an explicit "yes."**

```
About to write:

01-identity/
  SOUL.md, USER.md, PRINCIPLES.md

02-context/
  company.md, domain.md, vocabulary.md, projects.md

03-skills/
  README.md

04-memory/
  README.md
  bootstrap-progress.md

05-connections/
  <each system>.md

06-agents/
  README.md                    (roster)
  chief-of-staff/              AGENT.md + triage-request, clarify-intent,
                               route-to-agent, execute-send, run-daily-digest
  validator/                   AGENT.md + memory/README.md
  skeptic/                     AGENT.md + memory/README.md
  voice-reviewer/              AGENT.md + memory/README.md   (only if accepted in 4.6)
  <each specialist>/           AGENT.md + memory/README.md
  <agents with automations>/   automations/<name>.md, each with a ## Runner section

<subagent directory from 5.5>/
  <slug>                       one definition per specialist, each pointing at
                               06-agents/<slug>/AGENT.md. .claude/agents/<slug>.md
                               is the Claude Code form.
                               NO chief-of-staff entry. The omission is the rule.

<shim path from 5.5>           one line: "See AGENTS.md, single source of truth
                               for this Agentic OS." Nothing else in the file.

AGENTS.md                      (updated to point at the populated OS; the framework
                               rules already in it carry forward, not replaced)

Already shipped with the template. Confirm present, do not overwrite:
  00-deliverables/README.md
  00-tasks.md                  (empty table, ready for the first row)
  00-templates/README.md
  01-sops/                     README, deliverables, task-tracking, review,
                               parallel-work, automations
  03-skills/bootstrap-company/SKILL.md
  03-skills/add-new-agent/SKILL.md
```

### Registering the specialists so the lead can spawn them

`06-agents/` is documentation. It does not make anyone spawnable. The tool only knows an agent exists if that agent has a definition in the subagent directory captured in 5.5, so write one per specialist on the confirmed roster, including the Validator, the Skeptic, and the Voice Reviewer if it was accepted in 4.6.

**Write none for the Chief of Staff.** Say that out loud in the summary, in one line, so the omission reads as the rule from `AGENTS.md` rather than as something you forgot.

Each definition is a spawn card, not a second copy of the role. Keep it to about one screen:

- The slug, matching `06-agents/<slug>/`.
- **When to spawn it**, written as trigger conditions drawn from the purpose and the common request shapes captured in 4.5. This is what the lead matches a request against, so "handles pricing questions and competitor comparisons" beats "the marketing agent."
- **The tools it is allowed**, if the tool supports scoping them. This is where a reviewer that must not edit the work it reviews gets denied edit access, rather than being asked nicely not to.
- **A body** that names the agent, states plainly that it is not the Chief of Staff, points at `06-agents/<slug>/AGENT.md` as the definition that outranks anything in the card, carries the company hard nos from 2.4, names the agent's review exposure per `01-sops/review.md`, and reminds it that its final message is the return value handed back to whoever spawned it, not a note to a human.

Do not restate the role. The card points at `AGENT.md`. A card that grows its own copy of the scope is a second source of truth, it will drift out of sync with the roster, and nobody will notice which one the agent actually read.

Then write the shim file at the path from 5.5, containing the one line from `AGENTS.md` and nothing else.

---

## After scaffolding: handoff

1. "Company is live. Start any new conversation by reading `AGENTS.md`."
2. "Talk to the Chief of Staff. Every request enters there. Every other agent is registered with your tool and spawnable by name; the Chief of Staff deliberately is not, because it is the lead session you are already talking to."
3. "Deliverables land in `00-deliverables/YYYY-MM-DD-<slug>/` and get indexed in `00-tasks.md`."
4. "Every automation is `manual` until you wire a runner. Nothing is on a schedule right now."
5. "Want a deeper spec on any agent? Run `add-new-agent` on that role."
6. "Run `bootstrap-company` once. After this, use `add-new-agent` or edit files directly."

## Verification (required section)

Before declaring this skill done, confirm:

- [ ] All nine numbered folders exist, with a `README.md` where one is expected, plus `00-tasks.md` at the root.
- [ ] `01-identity/` has SOUL, USER, and PRINCIPLES with no template placeholders left. USER hard nos include: a draft is not a send, Chief of Staff is the sole sender, no money movement, major-client approval, no secrets movement, no destructive data actions.
- [ ] `01-identity/USER.md` records the writing conventions from 1.6, and they are not contradicted anywhere in the scaffold.
- [ ] `02-context/company.md` synopsis matches what the principal said in 1.2.
- [ ] Every agent in `06-agents/README.md` has an `AGENT.md` with: Role, Top 3 responsibilities, Scope in and out, Default loop, Common request shapes, Escalation, Skills, Automations, Success criteria, Verification.
- [ ] `06-agents/validator/` and `06-agents/skeptic/` exist. `06-agents/voice-reviewer/` exists if and only if the principal said yes in 4.6.
- [ ] Every reviewer's `AGENT.md` states that it is output-facing and points at `01-sops/review.md` rather than restating the contract.
- [ ] Every specialist on the confirmed roster, including the Validator, the Skeptic, and the Voice Reviewer if it was accepted, has a definition in the subagent directory named in 5.5, and each one points at its own `06-agents/<slug>/AGENT.md`.
- [ ] There is **no** `chief-of-staff` entry in that directory, and the Phase 7 summary named that omission as deliberate.
- [ ] The shim file named in 5.5 exists, holds the single line pointing at `AGENTS.md`, and duplicates no OS content.
- [ ] If the tool has no subagent mechanism, or the principal has not picked a tool, that is recorded in `04-memory/bootstrap-progress.md` and was named in the handoff, along with what it costs the review layer. No directory or shim was invented to satisfy this checklist.
- [ ] The Chief of Staff has all five default skills and a routing table covering every common request shape captured in Phase 4.
- [ ] Every connection file has Purpose, Mechanism, Auth, and Allowed operations. No secret values appear in any of them.
- [ ] Every automation lives under its owning agent's `automations/` folder, **has a `## Runner` section**, and is draft-only or signal-only for anything externally visible.
- [ ] The status table in `01-sops/automations.md` lists every automation and matches the per-file runner declarations.
- [ ] `00-tasks.md` still has its header and column row, and no invented example rows.
- [ ] `01-sops/` is unmodified and its five SOPs plus README are present.
- [ ] `04-memory/bootstrap-progress.md` records the interview answers, so a future session can audit the choices.
- [ ] No identity, context, connection, or agent file was written before the Phase 7 confirmation.

## Anti-patterns

- **Skipping phases to save time.** Each phase feeds the next. Skipping the domain phase makes the team phase generic.
- **Batching questions.** A 30-question form is not an interview. One at a time, every time.
- **Writing OS files mid-interview.** Only Phase 7 writes. Phases 1 through 6 stage progress in `04-memory/bootstrap-progress.md` and nowhere else.
- **Inventing the company.** When the principal hesitates, propose options. Do not assume answers.
- **Letting "out of scope" stay empty for any agent.** Out of scope drives routing more than in scope does.
- **Generic success criteria.** "Does the job well" is not measurable. Push for observables.
- **Skipping the Chief of Staff.** It is the entry point. Non-negotiable.
- **Creating a Chief of Staff subagent.** Only the lead session can spawn. A Chief of Staff that cannot dispatch is a dead end.
- **Scaffolding the roster and never registering it with the tool.** `06-agents/` is documentation. Until each specialist has a definition in the subagent directory, nobody is spawnable and one session role-plays the whole company from a single context. Review then degrades to the same context re-reading its own draft, which is the self-grading `01-sops/review.md` exists to replace, and it degrades silently because the ceremony still runs.
- **Scaffolding the Chief of Staff without `execute-send` and `run-daily-digest`.** Those two are what make it the front door rather than a router.
- **Scaffolding an automation with a cron expression and no runner.** The file will read as scheduled, nothing will fire it, and nobody will find out until the output has been missing for a month.
- **Skipping the review layer because the company is small.** A one-person company is exactly where an unchecked wrong number reaches a customer fastest, because there is no second human in the loop. Validator and Skeptic are cheap. Scaffold them.
- **Overwriting the shipped framework files.** `01-sops/`, `00-tasks.md`, and the two skills in `03-skills/` come with the template. Bootstrap confirms them, it does not rewrite them.
