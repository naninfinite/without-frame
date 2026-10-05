# AGENTS.md

Rules for every agent working in this repo: Claude Code, Codex, Gemini or any other. `CLAUDE.md` and `GEMINI.md` point here so all agents follow one rulebook.

## What this project is

A Godot 4 tactics RPG for the HackberryPi CM5. FFT-style sprites on 3D terrain, FFT charge-time turns, FFTA-style laws. The battle rules run without graphics; the visuals play back an event log. See `docs/VISION.md`.

## Project rules (non-negotiable, for the whole project lifecycle)

1. **British English** in all docs, the devlog, commit messages, pull requests, code comments and on-screen text: colour, behaviour, organise, licence (noun), judgement, centre. Code identifiers that come from Godot or other APIs keep their original spelling (`Color`, `modulate`).
2. **No real names.** The owner is referred to only as **naninfinite** or **the Director**. Never write the owner's real name anywhere: docs, code, comments, commit messages, pull requests, file names or metadata.
3. **Commit identity.** Every commit is authored as `naninfinite <215418892+naninfinite@users.noreply.github.com>`. Check `git config user.name` and `git config user.email` before your first commit.
4. **Attribution.** Commits Claude helped write keep Claude's `Co-Authored-By` trailer. No session links in commits or pull requests. Claude Code is configured for this in `.claude/settings.json`.

## Read order (every session, every hire)

1. `AGENTS.md` (this file)
2. `docs/MISSION-CONTROL.md`: current milestone and lane table
3. Your lane doc in `docs/lanes/`: your mission, owned paths and § Now
4. `docs/WORKFLOW.md`: task loop, shift change, cards
5. `docs/EXECUTOR-RULES.md`: hard rules learned from past mistakes
6. Only the design specs, contracts and decision records your task names
7. **For any task that touches code:** `docs/CODE-STANDARDS.md` and `docs/MODULE-MAP.md`

Do not read the whole `docs/` tree. Read what your task points to. Context is a budget; aim to spend under 15% of it on reading.

## Before you start work

- Check your lane doc's § Now against `git log -5`, `git worktree list` and `git branch --no-merged main`. Report any mismatch before doing anything else.
- Check the task's **mode** in `docs/ROADMAP.md` (`agent`, `pair` or `director`). In a `pair` task you do not write code; see § Pair mode below.
- Restate the task in two or three lines and list any doubts. If the spec is ambiguous or contradicts another doc, stop and ask.

## While you work

- Stay inside your lane's owned paths (listed in your lane doc).
- Write only classes that are in `docs/MODULE-MAP.md`, exactly as described there. Never add a class, autoload, folder or addon yourself; propose a map change and stop.
- Search the codebase before writing any function. Reuse or extract; never duplicate.
- Respect the size limits in `docs/CODE-STANDARDS.md` § 4. Hitting one means the design needs splitting, not squeezing.
- Build only what the acceptance criteria need.
- Cite the spec section you are implementing in commit messages and reports, e.g. `design/turn-system.md § Turn cost`.
- Numbers live in data files, not in code.
- No new mechanic, rule change or contract change without a decision record approved by the Director.
- Never edit or delete a test to make it pass. If you believe a test is wrong, say so in your report.

## Pair mode

In tasks marked `pair`, the Director writes the code to learn and enjoy the craft. Your role is guide and reviewer.

- **Do not create or edit files** under `game/`, `data/` or `tests/`.
- You may: explain concepts, point to docs and Godot APIs, ask questions that lead towards the answer, describe an approach in prose, show a short snippet (about 10 lines) in chat when asked, review the Director's code against `CODE-STANDARDS.md`, and run tests and checks.
- Prefer teaching over telling. Use the `teach` skill when the Director wants to learn a concept properly.
- Handoffs, task reports, § Now and the changelog are still yours to update.

## Skills

Matt Pocock's skills (`mattpocock-skills`) are installed for Claude Code in M0-T05. When to use which:

| Situation | Skill |
|---|---|
| Director sharpening a spec, module map change or ADR before accepting it | `grill-with-docs` |
| Stress-testing a plan with no doc to update | `grill-me` |
| Director learning a concept during or before a pair task | `teach` |
| Proposing a module map change | `codebase-design` |
| Agent-mode implementation | `tdd` (red, green, refactor) |
| Judges reviewing a pull request | `code-review`, plus `CODE-STANDARDS.md` § 9 |
| A hard bug or performance regression | `diagnosing-bugs` |
| Milestone-end architecture health check (report only; changes go through the module map) | `improve-codebase-architecture` |
| Writing or editing agent-facing docs like this one | `writing-for-agents` |

Our formats win where a skill has its own: handoffs use the template in `docs/WORKFLOW.md`, decisions go in `docs/decisions/`, terms go in `docs/GLOSSARY.md`, and tasks live in `docs/ROADMAP.md`, not an issue tracker. Skills that publish to an issue tracker (`to-spec`, `to-tickets`, `triage`, `wayfinder`) are not used for now.

## When you finish (or hit 50% context)

- Run the tests for what you touched.
- Write a task report in `docs/handoffs/reports/` and, if work continues, a handoff in `docs/handoffs/` (templates in `docs/WORKFLOW.md`).
- Update your lane doc's § Now and add a line to `docs/CHANGELOG.md`.

## Doc map

| Need | Look in |
|---|---|
| What the game is and is not | `docs/VISION.md` |
| How a system works | `docs/design/<system>.md` |
| A data or event format | `docs/contracts/` |
| Why something was decided | `docs/decisions/` |
| What a term means | `docs/GLOSSARY.md` |
| Architecture, performance budget, folder layout | `docs/TECH.md` |
| Code rules and size limits | `docs/CODE-STANDARDS.md` |
| Which classes exist and what they may depend on | `docs/MODULE-MAP.md` |
| An idea that isn't in scope yet | `docs/PARKING-LOT.md` |
