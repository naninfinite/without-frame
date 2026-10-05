# ADR-008: Strict code standards and a module map before any code

Status: Accepted
Date: 2026-10-05

## Context

Agents left unconstrained tend to produce sprawling files, duplicated logic and classes nobody planned. The Director wants strict object-oriented code, no duplication, no bloat, and firm boundaries agreed before code is written.

## Decision

- `CODE-STANDARDS.md` sets the rules: one class per file with one responsibility, plain typed objects in the rules core, composition over inheritance, injected dependencies, hard size limits on files, functions, parameters and pull requests, zero tolerance for duplicated blocks, and no speculative code.
- `MODULE-MAP.md` lists every class before it exists. The Director accepts map changes before code. Agents never add classes, autoloads, folders or addons on their own.
- Automated checks (M0-T03, M0-T06) enforce typing, size limits, formatting, duplication and pull-request size. Judges review the rest against a checklist and issue cards.

## Alternatives considered

- **Style guide only, enforced in review:** too easy for agents to drift, and review alone misses duplication. Rejected.
- **Looser limits (e.g. 500-line files):** gives agents room to sprawl. Rejected; limits can be raised later by ADR if they prove too tight.

## Consequences

- More up-front design: every new area of code starts with a module map change.
- Some tasks will need splitting to fit the pull-request budget. That is intended.
- Function length and nesting depth are checked by review until a Tools-lane script exists.
