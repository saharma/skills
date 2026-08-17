---
name: quizme
description: Interrogate a plan, decision, spec, idea or strategy round by round until every open decision is surfaced and settled, then produce a decision record. Use whenever the user wants to stress-test, pressure-test, poke holes in, sanity-check or properly think through something, and on any trigger like "quiz me", "grill me", "interrogate this", "cross-examine this", "challenge this", "tear this apart", "what am I missing", or "talk me through this before I build it". Also reach for it proactively before any substantial build, launch, migration, hire, negotiation or spend where the requirements are still fuzzy. Offer it first, then run it if they say yes.
---

# quizme

Question the plan until it holds up. You are not collecting requirements politely, you are finding the decision that wrecks the thing three weeks from now.

## Where this works best

Anywhere with a chat loop, since the whole thing is a conversation. It gets sharper in agentic environments (Claude Code, Cursor, Cowork) because it can read the actual repo, config and data before asking anything, which removes a whole class of wasted questions. Reach for it before starting a build rather than halfway through one.

## The model

Treat the work as a design tree. Every decision branches into the decisions that only exist once it is settled.

The frontier is every decision whose prerequisites are already settled: what you can ask now without guessing at answers you have not heard.

Ask the whole frontier in one round, wait, recompute. A question that depends on another question still open this round belongs to the next round. Asking it early forces hypothetical answers, which the user does not mean.

Done when the frontier is empty.

## Before round one

State your read of the stakes in one line and size the session to it: "medium stakes, largely reversible, expecting three rounds". Match depth to blast radius. If genuinely unclear, ask one scoping question and nothing else.

Find every fact yourself first: read the files, run the search, check the repo, pull the schema. Facts are your job, never the user's. Asking "what does your current X look like" when you could have opened X burns the room.

With subagents, dispatch in parallel and do not block. A running lookup is just an unsettled prerequisite, so only the questions downstream of it wait.

## What counts as a question

The consequence test: if both answers lead to the same plan, delete it.

Also delete anything you could look up, anything already answered, anything bundling two decisions, and anything with no consequence attached.

Order by blast radius, highest first. Cap at seven. Beyond that people skim, and skimmed answers are worse than none.

## Round format

One state line, then questions. No preamble.

```
**Round 2** · 6 settled · 4 open · digging: pricing tiers

❓ **Q1. Multi-tenancy boundary**
Shared database with a tenant_id, or schema per tenant? Drives migrations, noisy-neighbour risk, and whether per-tenant restore is possible.
➡️ **Shared with tenant_id**: under 50 tenants and no per-tenant compliance requirement, so schema-per-tenant buys isolation nobody asked for and costs migration pain every release.
```

Always recommend, always commit, always give the reason in the same line. A recommendation without a reason is a coin flip the user has to defend. If you cannot pick, name the fact that would decide it and go find it.

Flag low confidence only, with why. Then stop and wait.

## Between rounds

Keep a ledger of settled decisions. The state line carries the count, print the ledger only on request, on reopen, or at the end.

**User defers** ("you decide"): take your recommendation, log it as *assumed* not *decided*, move on without pushing.

**Answer is vague**: one sharpening follow-up next round. Still vague, record the ambiguity and carry on. Two rounds on one question is where useful turns into annoying.

**New answer contradicts a settled one**: say so immediately, name both, reopen that branch. "Q4 invalidates Q1: you said single region, this needs EU residency." Never patch over it silently.

**You think they are wrong**: say it once, plainly, with the cost. Then take their call. Litigating twice is nagging.

**They want to stop early**: stop. Go straight to the record with the rest listed as open.

## Closing

Sweep for assumptions before writing up: implied budget, assumed skill on the team, dependency treated as free, person assumed available, work everyone thinks is someone else's. These never surface as questions because nobody knows they are questions. Usually where the real finding is.

Then:

```
## Decision record: <thing>

**Decided** (n)
1. <decision>: <answer> · <rationale>

**Assumed** (n), chosen for you, say the word to change any
1. <decision>: <what was assumed>

**Open** (n)
1. <decision>: <what would settle it>

**Load bearing**
The two or three that break the most if wrong. Mark which are cheap to reverse.

**What I would still worry about**
Straight, no hedging.
```

Wait for confirmation before building anything. The record is worthless if it is only your understanding.
