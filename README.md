# Skills

Five Claude skills. Drop a folder into your skills directory, or install the packaged `.skill` file.

| Skill | What it does | Best in |
|---|---|---|
| `quizme` | Interrogates a plan round by round until nothing is silently assumed, then writes a decision record | Anywhere, sharper with repo access |
| `adr` | Architecture Decision Records, with the rejected options and the costs | Claude Code, Cursor |
| `application` | Tailors a CV and writes a cover letter against a specific advert, ATS-safe | Chat with file access |
| `interview-prep` | Turns an advert into the questions you will actually be asked, with answers from your real history | Chat |
| `reels` | Hook, script, on-screen text and caption for short-form video | Chat |

`application` and `interview-prep` need setup: they run on your real work history and your own rules about how it must be described. Both skills tell Claude to ask for that on first use.

## Install

**Claude Code / Cursor**: copy the folder into `.claude/skills/` in your project, or `~/.claude/skills/` for all projects.

**Claude.ai**: upload the `.skill` file and hit Save skill.
