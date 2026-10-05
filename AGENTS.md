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

Do not read the whole `docs/` tree. Read what your task points to. Context is a budget; aim to spend under 15% of it on reading.

## Before you start work

- Check your lane doc's § Now against `git log -5`, `git worktree list` and `git branch --no-merged main`. Report any mismatch before doing anything else.
- Restate the task in two or three lines and list any doubts. If the spec is ambiguous or contradicts another doc, stop and ask.

## While you work

- Stay inside your lane's owned paths (listed in your lane doc).
- Cite the spec section you are implementing in commit messages and reports, e.g. `design/turn-system.md § Turn cost`.
- Numbers live in data files, not in code.
- No new mechanic, rule change or contract change without a decision record approved by the Director.
- Never edit or delete a test to make it pass. If you believe a test is wrong, say so in your report.

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
| An idea that isn't in scope yet | `docs/PARKING-LOT.md` |
