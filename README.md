# Cursor Skills

Packaged Cursor agent skills. Each `.skill` file is a zip that contains a `SKILL.md` with instructions the agent follows when that skill is in play.

## Install

Copy a skill into one of these locations, then restart Cursor or reload skills:

| Scope | Path |
| --- | --- |
| Personal (all projects) | `~/.cursor/skills/<skill-name>/` |
| Project (this repo only) | `.cursor/skills/<skill-name>/` |

To unpack a packaged skill:

```bash
unzip adr.skill -d ~/.cursor/skills/
```

That extracts a folder such as `adr/SKILL.md`. Cursor loads skills from those folders, not from the `.skill` zip itself.

## Skills

### `adr.skill`

Writes Architecture Decision Records at the moment a technical choice is made, so the reasoning does not disappear into chat history.

Use when a design or architecture call is settled, or when someone asks to log a decision, write an ADR, or explain why a direction was chosen. Typical triggers: data model, framework, hosting, auth, integrations, build vs buy.

Each record is one decision, with context, options considered (including the ones that lost), the choice, and the costs. Accepted records are not edited later; a new ADR supersedes them.

### `application.skill`

Tailors a CV and cover letter to a specific job advert. Output is ATS-safe (single column, standard headings, no tables or graphics) and stays within hard rules about how experience is described.

Use when a job description, link, or role title is pasted in, or when asked to apply, tailor a CV, write a cover letter, or line experience up against a role.

The agent maps the advert's requirements to real evidence, mirrors the employer's wording for ATS matching, and flags gaps in chat rather than inventing them on the page.

### `interview-prep.skill`

Turns a job advert or interview invite into the questions likely to be asked, with answers built from real work history rather than generic filler.

Use for screens, panels, take-homes, AI-evaluated assessments, post-interview debriefs, or when asked to prep, predict questions, or help with answers.

Delivers eight to twelve likely questions, draft answers in a speakable voice, flags weak spots honestly, and finishes with questions to ask the employer. Can also run as a live mock, one question at a time.

### `quizme.skill`

Stress-tests a plan, decision, spec, idea, or strategy round by round until open decisions are surfaced and settled, then writes a decision record.

Use when asked to quiz, grill, interrogate, pressure-test, or sanity-check something, or before a substantial build, launch, migration, hire, negotiation, or spend while requirements are still fuzzy.

Each round asks the current frontier of decisions (cap seven), recommends a call with a reason, then waits. It closes with decided, assumed, and still-open items, plus what would still be worrying.

### `reels.skill`

Writes short-form video content (Reel, TikTok, short) in a direct, dry voice: hook, body beats, on-screen text, caption, and a payoff only if there is a real ask.

Use when asked for a Reel, TikTok, script, hook, caption, or content idea, when launching or promoting a product or event, or when a draft sounds too corporate.

Default is three genuinely different variants, written for sound-off first, with no brand-speak and no claim a product does not actually ship.

## License

Personal skills, published as-is. Use or adapt as you like.
