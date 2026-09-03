---
name: add-new-agent
description: Spin out one new specialist agent into an existing roster. Use when an existing agent's lane visibly cracks (overflow, missed cadence, a real specialty need) or when an "escalate to the principal" route becomes recurring enough to deserve its own owner.
when_to_use: After bootstrap is complete and the OS is populated. Run it for a lane that is not already owned by someone on the roster. Do not use it to re-add an existing role, and do not use it to split a role that still has capacity.
---

# Add a New Agent

A short, focused interview that adds one agent to the roster without re-running the full bootstrap.

## Before you start

- **Confirm the OS is populated.** `01-identity/` and `06-agents/chief-of-staff/` must exist. If they do not, run `bootstrap-company` instead.
- **Confirm the lane is genuinely needed. The default answer is no, route through the Chief of Staff.** Adding an agent because a request felt awkward once is sprawl. The routing table absorbs a lot before a new role is warranted.
- **Read the current roster** in `06-agents/README.md`, including any "future agents" list, so the new agent does not overlap an existing lane. Overlap is worse than a gap: two agents who both half-own something will each assume the other has it.
- **Every new agent inherits the company hard nos** from `AGENTS.md` and `01-identity/USER.md`. These are not negotiable per role:
  - A draft is not a send. Specialists draft. The Chief of Staff is the sole sender, after explicit approval.
  - No money movement by any agent.
  - No commitment to a client without approval.
  - Major-client actions need approval, including routine ones.
  - No moving or sharing secrets.
  - No destructive data actions.

## What counts as a cracked lane

Add an agent when at least one of these is observable, not anticipated:

- An existing agent is missing its own cadence because a second kind of work keeps preempting it.
- The same request shape has escalated to the principal three or more times, and the escalation was routing, not judgment.
- The work needs domain depth the existing agent's `AGENT.md` explicitly puts out of scope.

Add an agent when you can name the evidence. "It seems like we'll need one" is not evidence.

## Interview

One question per turn. Reflect each answer back before advancing.

### 1. Trigger

> "What's prompting this addition? Is an existing agent overloaded, or is this a recurring escalation that needs its own owner? Be specific: name the lane that's cracking, or the request shape that keeps escalating."

If the answer is a hypothetical, stop here and recommend routing through the Chief of Staff instead.

### 2. Role name

> "What's the agent called? Prefer a role that isn't already on the roster. Current owners are: <list from `06-agents/README.md`>."

### 3. Purpose

> "One sentence: why does this role exist?"

### 4. Top 3 responsibilities

> "Three things this role owns end to end."

Three, not seven. A role with seven responsibilities is two roles or a wish list.

### 5. Out of scope

> "What is NOT this role's job, even though someone might assume it is? Must include: no external sends, no money movement, and no becoming a second front door. The Chief of Staff stays the only entry point."

### 6. Common request shapes

> "Three concrete things you'd ask this agent in a normal week. These become rows in the Chief of Staff's routing table."

### 7. Escalation

> "When should this agent stop and check with you? The defaults are all the company hard nos, plus: a draft is not a send, the Chief of Staff is the sole sender, no money movement, major-client approval. What else?"

### 8. Routing impact

> "What routes in the Chief of Staff's table move from 'escalate to the principal', or from another agent's lane, to this new agent?"

A new agent with no routing changes is a new agent nobody will use.

### 9. Skills

> "What skills does this agent need on day one? We can add more later. Every skill ends with a Verification section."

### 10. Automations

> "Any recurring work this agent owns on a schedule? Optional, and most new agents start without any. If yes, each one needs a runner per `01-sops/automations.md`, and the honest default is `manual`. Automations produce drafts or signals, never sends."

### 11. Review exposure

> "Will this agent's output hit any of the five review triggers: a number, a named client, a public claim, an external send, a strategy shift? If yes, its deliverables go through `01-sops/review.md` like everyone else's."

Reviewers themselves are not added through this skill. They are scaffolded at bootstrap.

## Confirm and scaffold

Show a single summary:

```
About to write:

06-agents/<agent-slug>/
  AGENT.md
  skills/
    <skill-1>/SKILL.md
    <skill-2>/SKILL.md
  memory/README.md
  automations/                        (only if any)
    <automation-name>.md              (each with a ## Runner section)

Updated:
  06-agents/chief-of-staff/AGENT.md   (new routing-table rows)
  06-agents/README.md                 (roster line added; removed from
                                       "future agents" if it was listed)
  01-sops/automations.md              (status table row, only if automations)
  <tool subagent directory>/<slug>    (definition, so the lead can spawn it)
```

Wait for an explicit "yes" before writing anything.

## Verification

- [ ] The agent folder exists with `AGENT.md`, `skills/`, and `memory/`.
- [ ] `AGENT.md` has every required section: Role, Top 3 responsibilities, Scope in and out, Default loop, Common request shapes, Escalation, Skills, Automations, Success criteria, Verification.
- [ ] Scope and Escalation encode the company hard nos: a draft is not a send, Chief of Staff is the sole sender, no money movement, major-client approval, no secrets movement, no destructive data actions.
- [ ] If the agent overrides an SOP, the override is in an explicit `### Overrides` subsection naming the SOP.
- [ ] The Chief of Staff routing table has at least one new row pointing at this agent.
- [ ] `06-agents/README.md` lists the new agent, and the "future agents" list is updated if it was there.
- [ ] No skill or responsibility duplicates an existing agent's lane. Check this by reading the other agents' "Scope: out", not just their "Scope: in".
- [ ] Every new `SKILL.md` ends with a Verification section.
- [ ] Every new automation has a `## Runner` section, and the status table in `01-sops/automations.md` matches it.
- [ ] The agent has a definition in the tool's subagent directory so the lead session can spawn it, and this is not the Chief of Staff.

## Anti-patterns

- **Adding an agent to a lane that hasn't visibly cracked.** "Just in case" agents are sprawl. They dilute the routing table and every one of them is context the Chief of Staff has to hold.
- **Re-adding a role that already exists**, or splitting one role into three when the original still has capacity. Wait for real overflow, then split along the seam that actually tore.
- **Forgetting to update the routing table.** An agent the Chief of Staff does not route to is invisible, and the work keeps landing where it was already landing.
- **Letting the new agent become a second front door.** The Chief of Staff stays the only entry point. A specialist that starts taking requests directly breaks the routing discipline for everyone.
- **Giving the new agent send or money powers.** Specialists draft. That rule has no exceptions and no per-role carve-outs.
- **Copying another agent's `AGENT.md` and editing the nouns.** The result reads plausible and routes badly, because the scope boundaries came from a different job.
