# Contributing To Touchstone

Touchstone should change only when a real work record shows that its claim and
evidence boundary is unclear, too broad, or fails to protect a meaningful
decision.

## Useful Contributions

- A reproducible false-green fixture with a smallest discriminating witness.
- Evidence that a claim exceeded inspection, build, seam, runtime, or physical
  evidence.
- A domain corpus that tests the present software-weighted examples.
- A scoring or reproduction correction that preserves the evidence boundary.
- Clearer documentation that does not change the frozen v1 behavior.

## Before Opening A Pull Request

1. Start from the intended integration base on a feature branch.
2. Keep unrelated work out of the branch.
3. State the claim/evidence gap being addressed and its evidence class.
4. Run the closest safe real exercise before adding regression coverage for a
   behavior change.
5. State what ran, what was observed, what was not run, and what remains owed.
6. Run `git diff --check` and inspect the full base-to-head commit and path
   range.
7. Push the exact head and open a draft pull request.

Changes to `SKILL.md` require a compatibility decision and independent review.
Do not turn Touchstone into a parser, status machine, permission layer, workflow
engine, or a demand for maximum proof on every claim.

By submitting a contribution, you agree that it may be licensed under this
repository's Apache License 2.0.
