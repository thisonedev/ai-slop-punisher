# AI Slop Punisher

An agent skill that scores technical writing (docs, blog posts, guides,
tutorials, code samples, READMEs) against common AI-writing patterns, quotes
every hit, and applies minimum edits that preserve the writer's voice.

The skill follows the [Agent Skills](https://agentskills.io/) format.

## Install from GitHub

```bash
npx skills add thisonedev/ai-slop-punisher
```

### Manual install

Copy (or symlink) `skills/ai-slop-punisher/` into your agent's skills directory:

- Claude Code: `.claude/skills/` or `~/.claude/skills/`
- OpenAI Codex: `.agents/skills/` or `~/.agents/skills/`
- Cursor: `.cursor/skills/` or `~/.cursor/skills/`

## Usage

Paste a draft or point the agent at a file, and ask whether it sounds like AI.
The skill returns:

- a score from 0 to 100
- a quote of each line that broke a rule, with a one-line fix
- an edited draft, if you ask for one

## Scoring

The ruleset has thirty-seven rules in seven groups. A draft starts at 100 and
loses 4 points for each rule that fires. Fabrication is the one critical rule:
if it fires, the score is capped at 30.

| Score | Band |
| --- | --- |
| 90 to 100 | ready to publish |
| 70 to 89 | light polish |
| 50 to 69 | solid rewrite |
| below 50 | back to the drawing board |

The full ruleset is in [`skills/ai-slop-punisher/SKILL.md`](skills/ai-slop-punisher/SKILL.md).

## Evaluations

[`evals/evals.json`](evals/evals.json) has three test scenarios with the
behavior the skill should show on each: a draft full of AI patterns, a draft
with none, and a draft that states facts its source does not.

## License

MIT.
