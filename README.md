# rnd-execution

> Evidence-gated R&D execution for agent-led research work.

A [Hermes Agent](https://hermes-agent.nousresearch.com) skill that codifies a
discipline for running research & development work with agents:
hypothesis → experiment → measurement → decision — with fair comparison
budgets, source-tagged claims, a decision ledger with mutation receipts, and
clean session/document hygiene.

The method rests on seven rules (*kaideler*): talk before building,
single-variable experiments, fair-comparison budgets, measure don't infer,
keep real records, report conflicts, and cost-gate long runs — anchored by a
noise-floor protocol (≥3 seeds before any headline claim) and freeze rules
for measured mechanisms.

**Language:** `SKILL.md` (the canonical distribution copy) is in English; the
original Turkish text is preserved verbatim in [`SKILL.tr.md`](SKILL.tr.md).

## What it's for

- Running experiment/research programs end to end
- Locking mechanisms behind micro-tests and keeping the lock honest
- Debugging "this decision broke — what else must change?" via mutation receipts
- Keeping one living handbook and records digested clean between sessions

**Not for:** one-off scripting/tooling, or product feature work without
measurements.

## Installation

Hermes skills are `SKILL.md` files loaded from a personal skills directory. To
use this skill with [Hermes Agent](https://hermes-agent.nousresearch.com/docs):

1. Copy the skill folder into your personal skills directory:

   ```sh
   mkdir -p ~/.hermes/skills/research/rnd-execution
   cp SKILL.md ~/.hermes/skills/research/rnd-execution/
   ```

2. Start a new Hermes session (the skill index is built at session start).

Some Hermes releases also support installing skills through the CLI
(e.g. `hermes skills install ...`) — check `hermes skills --help` and the docs
for the exact flow your release supports; manual placement as above works
regardless.

Then reference `rnd-execution` in a session or in your project instructions to
have the agent follow the discipline.

## Contents

- `SKILL.md` — the full skill (English, canonical): when to use, the seven
  rules, noise floor & freezing, decision ledger + mutation receipts, session
  ritual, pitfalls, verification checklist
- `SKILL.tr.md` — the original Turkish text, preserved verbatim
- `LICENSE` — MIT

## License

MIT — see [LICENSE](LICENSE).