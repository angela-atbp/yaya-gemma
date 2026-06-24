# Yaya Gemma — Prompt Audit & "Prompt Better" Guide

*Reviewing your opening prompts across the project, grouped by theme. Per prompt: what I understood · what you missed · how to prompt it better.*

---

## ⭐ Read this first — the 3 patterns costing you tokens

Your prompts are above average. You almost always give role, context, constraints, and an output format. The waste isn't weak prompting — it's three repeated habits:

**1. You drip-feed multi-part changes across several messages.**
On at least 4 occasions (protein-variety fix, recipe-page redesign, FB replies, spec conversion) your follow-ups were things you already knew at the start. Each follow-up = a full regeneration / re-audit. *Bundle everything you already know into turn one as a numbered list.* This is your single biggest token saver.

**2. You name the deliverable instead of the decision the deliverable must support.**
"Rewrite the origin story" → what you needed was "reconcile two conflicting strategy docs into one testable charter." Leading with the *decision* skips a whole clarification round. (You saw this yourself in the charter chat.)

**3. You let me pick business levers you should pin.**
Repeatedly I had to choose a credit price, a gating rule, a budget. When I choose, you get a guess you then have to correct. *Pin the number/rule in the prompt* ("advice = 2 credits", "free tier = 1 substitution") and the first output is final.

**Plus two cheap mechanical wins:**
- **Conversation hygiene:** several chats ran 5–6 major items long. Long chats degrade response quality and burn context re-reading themselves. One unit of work = one chat. Reference past work by file/ticket ID, not by keeping the thread alive.
- **Skill invocation:** when you invoke a skill (`/yaya-gemma-code-auditor`) for a *narrow* task, I read the whole skill then explain why I'm not using it fully. Say "narrow audit, skip the 5-section report" up front and you save the detour.

---

## Theme 1 — Engineering / Lovable prompts (your highest-volume use)

Chats: recipe routing, protein variety, week-plan quality, AI-only consolidation, onboarding dead-ends, recipe-page AI redesign, session logging, analytics, code audits.

**What you do well:** structured problem statements (Context / Goal / Task / Success measure / Expected Outcome), naming target files, stating guardrails (no extra Gemini calls, 375px, 44px touch targets), asking for e2e tests. This is genuinely strong dev briefing.

**What you repeatedly miss:**
- **The business lever inside the technical task** (credit price, free-tier limit, gating). Pin it.
- **Which onboarding/system is live** when two exist — you make me discover it. If you know "the `/onboarding` route uses Onboarding.tsx", say so; it saves an audit pass.
- **Deploy-state preconditions.** Several fixes depended on whether a *previous* fix was already deployed. State "fix-pass-2 is live" or "unsure, check" — otherwise I hedge.
- **Scope of the audit skill.** You invoke the full auditor for narrow jobs. Add "focused fix, not the full report."

**Better template for a Lovable bug/feature:**
> **Role:** Lead dev. **Scope:** [one feature/bug only].
> **Live code state:** [what's deployed / which system is routed].
> **Problem:** [symptom + where].
> **Business rules to honor:** [credit cost, free/premium gate, the exact number].
> **Target files (extend, don't rewrite):** […].
> **Guardrails:** no new LLM call if X; 375px/44px; allergy filter before scoring.
> **Output:** one Lovable .md (paste-ready, e2e tests included) + a separate reference doc for any TODOs assigned to me.

> *Why it's better:* pins the levers I otherwise guess, tells me what's live so I don't re-audit, and pre-scopes the skill.

---

## Theme 2 — Product / UX / strategy specs

Chats: pantry page AHA, adaptive meal planning, weekly-plan framework, spec conversion, lifecycle moments.

**What I understood (representative — pantry AHA):** review the doc, produce an improved version whose job is a faster AHA, output feeding Claude Design.

**What you do well:** you state *who consumes the output next* (Claude Design, Lovable, the team). That's a pro move — it changes the format I produce. Keep doing it.

**What you miss:**
- **Whether you want diagnosis + fix, or just fix.** Your best results came when you said "establish the framework *before* the solution" (week-plan chat). Make that explicit every time: "challenge the spec first, then build."
- **The downstream tool's context limits.** Claude Design won't have your source docs; you sometimes reference data ("E.Leclerc test data") it can't see. Either paste a sample or tell me to genericize.
- **Conventional vs. your-labelled Vision/Mission.** You twice inverted the conventional definitions; I had to ask. State "use my labels literally" or "use conventional structure."

**Better framing:** lead with the *decision the artifact must support*, not its name. "I need a pantry brief Claude Design can build from with no other context — diagnose why the AHA is weak, then give design-actionable fixes."

---

## Theme 3 — Marketing copy & community (Angela's voice)

Chats: FB acquisition posts, re-engagement, group replies, weekend broadcast email, new-channel playbooks.

**What you do well:** the persona rules live in your project instructions, so I rarely get the voice wrong. You also give the platform and the specific group culture, which is exactly right.

**What you miss / what costs turns:**
- **Micro-edits arrive one at a time.** The FB-reply chats show 4–5 sequential tweaks ("drop sans carte bancaire", "add 'I'm listening'"). Each is a full tool call. Batch your instinctive edits: "warm, no salesy phrasing, include a 'tell me everything' line, keep under 2 lines."
- **You don't always say link-yes/link-no.** The whole comment-gated strategy hinges on it. State it: "public reply, no link/code."
- **You don't specify variant count.** I default to 2–3. If you want one paste-ready line, say "one final version."

**Better framing:** "Angela's voice, [platform/group]. [Link or no link]. Constraints: [no salesy words / under N lines / include X]. Give me ONE final version, not options."

---

## Theme 4 — Brand & foundational docs

Chats: vision/mission, why-we-exist charter, team About-Us, onboarding kit, logo assets.

**What you do well:** you give the audience (team vs. customer vs. investor) and the doc's *job*. Strong.

**What you miss:**
- **Reward/equity/ownership facts** you alone can confirm — I have to tag `[ANGELA TO CONFIRM]`. If you have them, give them; if not, that's fine, just know each one is an open loop.
- **Source-of-truth conflicts.** You have multiple overlapping strategy docs (PDF vs KB vs charter). When they conflict I either pick one or flag it. Tell me which is canonical up front.
- **Logo:** you didn't specify italic lines, whether the gold dot survives in mono, format set. Pre-answering those three = no back-and-forth.

---

## Theme 5 — Business / "should I…" advisory

Chats: paid ads for PMF (×2), CTO co-founder, VC profile, competitors, blog tooling.

**What you do well:** you invoke the right advisor skill and state the underlying goal ("validate PMF", "get 20 sticky users"). That lets me challenge the *premise*, which is what you say you want.

**What you miss:**
- **The metric/number that makes the answer concrete** (current signups, retention, budget). "Small ads" + "validate PMF" forced me to assume your numbers. One figure shifts the whole answer.
- **Scope-fit.** The co-founder/VC/legal questions don't belong in the product project — they pollute its context and memory. Open a separate chat (I flagged names each time).
- **For competitor/research asks:** add "apps I list **plus** any you find" so you get KB + fresh research, not just one.

---

## Your one-line upgrades, per theme

| Theme | The single highest-value addition |
|---|---|
| Engineering | Pin the business number (credit cost / gate) + state what's live |
| Product/UX | Lead with the decision the doc must support; say "diagnose, then build" |
| Marketing | Batch your edits; state link-yes/no and variant count up front |
| Brand | Name the canonical source doc; supply founder-only facts |
| Advisory | Give one real metric; put it in its own chat |

---

## The universal opening line that would fix ~80% of your re-rounds

> "Here's everything I already know, as a numbered list: [1…2…3…]. Pin these as decided, don't ask me to choose them. Scope = [one thing]. Output = [format] for [who consumes it next]. Challenge anything weak before you build."

That one habit — front-loading what you already know and explicitly forbidding me from re-asking it — collapses most of your multi-turn chats into one.

---

## Two housekeeping notes on *this* chat

- **Name:** suggest `process_prompt_audit_claude_usage_260624` (matches your convention).
- **Scope:** this is a clean standalone retro. Don't reuse it for product work — start fresh and reference this file by name.
