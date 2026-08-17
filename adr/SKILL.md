---
name: adr
description: Write Architecture Decision Records that capture a significant technical decision, the options rejected, and the consequences. Use whenever a design or architecture choice gets made in conversation, whenever the user says "write this up", "log this decision", "ADR", "why did we choose", or asks to document a technical direction. Also reach for it proactively right after any hard call on data model, framework, hosting, auth, integration or a build versus buy question, before the reasoning gets lost.
---

# ADR

An ADR records one decision at the moment it is made. The code will always show what was chosen. What vanishes is why, and what was already ruled out. Six months later someone looks at the design, thinks the obvious alternative was never considered, and either relitigates a settled call or repeats a mistake. The record exists to stop that.

## Where this works best

In a coding agent with repo access (Claude Code, Cursor, Codex), because it can read the existing `adr/` directory for the next number and the house wording, then commit the file alongside the change it describes. It works in a plain chat window too, you just paste the decision in and save the output yourself. Pairs naturally with a design interrogation: run one of those first, then write an ADR per load-bearing decision that came out of it.

## What earns an ADR

Write one when the decision is expensive to reverse, constrains later work, or would surprise a competent engineer reading the code cold. Data model shape, tenancy boundary, auth approach, interchange format, hosting, framework, build versus buy, anything deliberately not built.

Do not write one for a decision with no live alternative, or one you could undo in an afternoon.

## Format

Fixed. Every record identical, so the set can be skimmed.

```
# ADR-0019: <decision in a short noun phrase>

**Date**: <YYYY-MM-DD>
**Status**: Accepted
**Supersedes**: <ADR number, or omit>

## Context
What forced a decision now. The constraints in force at the time: scale, team, budget, deadline, regulation, existing systems. Write this so it still makes sense to someone who was not there. Facts, not narrative.

## Options considered
1. **<Option>**: what it is, why it was attractive, why it lost.
2. **<Option>**: same.
3. **<Chosen option>**: same, ending in why it won.

## Decision
One paragraph. What was chosen, stated plainly, in the present tense.

## Consequences
What this buys. What it costs. What it now rules out or makes expensive later. What has to be true for this to keep being the right call, which is the line that tells a future reader when to revisit.
```

## Rules

- **One decision per record.** Two decisions is two records, even when made in the same breath.
- **Options considered is the point.** A record with one option is a note, not a decision. If only one option was ever on the table, say so and say why the others were never viable.
- **Consequences must include the costs.** A record listing only upside is marketing. Whatever the chosen option is worse at, write it down.
- **Never edit an accepted record.** Reality changing does not make the old reasoning false, it makes it superseded. Write a new record, set its Supersedes field, and change the old one's status to Superseded and nothing else.
- **Number sequentially, zero-padded to four digits.** Never reuse a number.
- **No em dashes.**
- Keep it to one page. If it runs longer, the context section is probably carrying narrative it does not need.

## Statuses

`Proposed` while still open, `Accepted` once acted on, `Superseded by ADR-NNNN` when replaced, `Deprecated` when the thing it governs is gone. Nothing else.

## Method

1. Check the existing records for the next number, the house wording, and whether this decision supersedes an earlier one.
2. If the options were not discussed explicitly, reconstruct them and put them to the user for confirmation before writing. Inventing a rejected option is worse than omitting one.
3. Draft, then reread the consequences section specifically and ask whether a reader would learn anything from it that they could not guess.
4. Save as `adr/NNNN-short-slug.md` alongside the others unless told otherwise.
