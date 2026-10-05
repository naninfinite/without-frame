# Workflow

How work moves through this project. Short on purpose.

## The task loop

1. **Idea.** Anything new goes into `PARKING-LOT.md`. Never straight into code.
2. **Promote.** At milestone planning the Director promotes ideas into tasks in `ROADMAP.md`. Each task gets an ID (`M1-T04`), an owning lane, a mode (below), a spec reference and acceptance criteria.
3. **Spec and map first.** If the task changes a mechanic, contract or architecture, the design doc and a decision record are updated before any code. If it needs a new class, `MODULE-MAP.md` is updated and accepted first.
4. **Build.** One lane writes (or the Director, in a pair task), on its own branch and worktree.
5. **Review.** A model from a different family reviews the diff against `CODE-STANDARDS.md` § 9. Judges run the checks.
6. **Playtest.** The Director plays it on the Hackberry.
7. **Merge.** Then: changelog line, lane § Now updated, task ticked in `ROADMAP.md`.

## Task modes

| Mode | Who writes the code | The agent's role |
|---|---|---|
| `agent` | An agent in the owning lane | Writes, tests, reports |
| `pair` | The Director, by hand, to learn and for fun | Guides, explains, reviews, runs checks. Never edits code files (`AGENTS.md` § Pair mode) |
| `director` | No game code | Decisions, docs, spikes |

Good pair tasks are small, central and educational, e.g. the rules core skeleton or the charge-time clock. The Director can switch a task's mode at any time by updating `ROADMAP.md`.

Pair tasks still follow every rule in `CODE-STANDARDS.md`, go through review, and get a task report (written by the agent from the session).

## Opening a pull request

1. Push the branch: `git push -u origin <branch>`.
2. `gh pr create --fill`, or open it on GitHub. The description says what changed, which spec sections it implements, and the task ID.
3. Wait for checks (once M0-T03 and M0-T06 exist) and the cross-family review.
4. `gh pr merge --squash --delete-branch`, then `git switch main && git pull`.

## Branches and worktrees

- Branch name: `<lane>/<task-id>-<slug>`, e.g. `mech/M1-T04-charge-time`.
- One worktree per active lane.
- `main` is protected: merge by pull request only, checks must pass.
- A lane only touches the paths its lane doc lists. A planned check (M0-T06) fails any pull request where a branch touches paths outside its lane.

## Shift change (routine, at ≥ 50% context)

The current agent stops starting new work and writes a handoff to `docs/handoffs/<task-id>-<slug>.md`:

```
# Handoff: <task-id> <title>
Shift: <n>   From: <model>   Date: <yyyy-mm-dd>

## State
What is done, what is half-done (with file paths).

## Decisions made this shift
Each with the reason. Link any ADR.

## Open questions
Anything the next shift must ask the Director.

## Next step
The single next action.

## Files touched
## Verify with
The exact commands that prove the current state (tests, scripts).
```

The new hire follows the read order, then the handoff, runs the verify commands, restates the task and lists doubts before touching anything.

## Task report (every finished task)

Written to `docs/handoffs/reports/<task-id>.md`: what was built, spec sections implemented, tests added and run with results, anything deviating from spec, and follow-ups for the parking lot.

## Cards (Judges)

Judges review agent conduct the way an FFTA judge reviews a battle.

- **Yellow card:** a minor breach, e.g. touched a file outside its lane or skipped the changelog. Noted in the task report. The agent continues.
- **Red card:** off-spec work, hallucinated APIs or facts, edited tests to pass, or ignored a stop condition. The agent is fired: work stops, the branch is frozen, and an incident note is written.

Incident note, in `docs/incidents/<yyyy-mm-dd>-<slug>.md`:

```
# Incident: <slug>
What happened:
Why it happened:
Rule that would have prevented it:
```

The rule is added to `EXECUTOR-RULES.md`. A fresh hire restarts from the last good handoff. Every firing makes the next hire better.

## Decisions

A decision record (`docs/decisions/ADR-NNN-<slug>.md`) is needed for any change to a mechanic, contract, architecture or lane structure. Records are never edited after acceptance, only superseded by a newer one that links back.

## Rituals (Director)

| When | What | Time |
|---|---|---|
| Start of session | Read `MISSION-CONTROL.md` and the relevant lane § Now | 2 min |
| End of session | Check the agent updated § Now and the changelog. Write or dictate the devlog entry | 5–10 min |
| Weekly | Skim the changelog, triage the parking lot, check milestone progress, prune `EXECUTOR-RULES.md` if it's bloating | 10 min |
| Milestone end | Retro in the devlog, plan the next milestone, decide whether any lane needs splitting | 30 min |
