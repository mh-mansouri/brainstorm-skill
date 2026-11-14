# brainstorm: a planning-only skill for Claude Code

A small [Claude Code skill](https://docs.claude.com/en/docs/claude-code/skills) for planning turns: ideas, strategy,
choosing topics, a step plan or a calendar. It keeps planning and doing apart: the skill plans, a later turn does the work.

## What it does

- Lists several options, picks the best one with a one-line reason, and gives short steps in order.
- Shows ideas as a table, most useful first, and names every step that needs your OK.
- Plans only: no posting, sending, rendering, deploying or code edits in that turn.
- Asks Claude Code to run the turn on a stronger model (`model:` and `effort:` in the frontmatter).

## Install

Copy the `brainstorm` folder to `~/.claude/skills/` (all projects) or to `.claude/skills/` in one project.
Edit `model:` in `SKILL.md` to the model you want for planning. Start it with `/brainstorm`, or let Claude pick it for
planning tasks.

## Does the model really switch? Test it yourself

We could **not** confirm the switch. Test it in your own setup before you rely on it:

1. Run one `/brainstorm` turn.
2. Open that session's log (`~/.claude/projects/<project>/<session>.jsonl`) and look at `message.model` on the replies of
   that turn. If it shows your normal model, the switch did not happen.
3. If your plan has a separate limit for the planning model, note its usage before and after the turn. No change means no
   switch.

## Our test (Nov 2026, 48 hours)

| What | Result |
|---|---|
| Runs | 7 planning turns, all started on the right kind of task |
| Plan only | Yes in all 7; no execution inside the skill turn |
| Errors or limit messages | None |
| Model switch | **Not confirmed**: the system note named the planning model, but the session logs recorded the normal model id |

So the planning-only behaviour works; the model switch may be a label only. Reports from other setups are welcome as issues.

## License

MIT, see [LICENSE](LICENSE).
