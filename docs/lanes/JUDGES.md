# Judges (`qa`)

Covers QA, the playtest log and agent cards. Also does Librarian work (doc drift checks) until that splits off.

## Mission

Nothing merges unless it is checked by someone who didn't build it. Keep the record honest: tests, playtests, cards and incidents.

## Owns (paths)

`tests/integration/`, `docs/playtests/`, `docs/incidents/`. Reviews (but does not write) `tests/rules/`.

## Never touches

Game code under `game/`, `data/`, `maps/`, `assets/`. Judges report problems; owning lanes fix them.

## Read for this lane

`WORKFLOW.md` § Cards, `EXECUTOR-RULES.md`, `TECH.md` § Testing, the design specs' worked examples, the task report under review.

## Duties

- Review every pull request with a model from a different family than the author.
- Check each worked example in `docs/design/` has a matching test with the same numbers.
- Issue yellow and red cards per `WORKFLOW.md`; write incident notes for red cards.
- Keep the playtest log from the Director's device sessions in `docs/playtests/`.
- Weekly: a drift check comparing code against the design docs; list mismatches in a report.

## § Now

Not started.

## Waiting on

M0-T01 (Godot project init).

## Next tasks

- M0-T03: GdUnit4 installed, headless runs locally and in a GitHub Action on every pull request.
- Map checker and asset checker specs (from `contracts/`) ready for M1.
