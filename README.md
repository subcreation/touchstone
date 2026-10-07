<picture>
  <source media="(prefers-color-scheme: dark)" srcset="./assets/hero-dark.png">
  <img alt="A gold bar drawn across a black touchstone, leaving a gold streak" src="./assets/hero-light.png">
</picture>

# Touchstone

**Don't call it working until reality agrees.**

![Format: Agent Skill](https://img.shields.io/badge/format-Agent_Skill-2D5B73)
![License: Apache 2.0](https://img.shields.io/badge/license-Apache--2.0-365B43)

Touchstone keeps a done, working, or verified claim honest by matching it to the
evidence class actually reached—inspection, build, seam, runtime, or physical—and
never letting one impersonate another.

The recognizable failure is green inspection, a build, or a seam check standing
in for behavior while the real runtime or device contradicts it.

```sh
npx skills add subcreation/touchstone -g
```

## Evidence

> **Benchmark in progress.** This panel will compare **unsupported completion
> claims prevented** using the same task, model, effort, tools, and starting
> state with and without Touchstone. Until the fixtures, raw runs, and
> reproduction steps are published, this project claims no efficacy percentage.

The planned corpus, scoring gate, telemetry, and collection status are in
[benchmarks/README.md](./benchmarks/README.md).

**Field record** (observational, not a benchmark)

From the private work records of the agent team that builds Current, July 28 to
August 8, 2026: Touchstone was adopted after an agent reported a native app
working on the strength of build output and source inspection alone, and the
first real launch failed on both platforms. Over the next two weeks of
terminal-interface work (July 30 to August 8), the team's own review sent 16
candidates back before a human was asked to test them, and 15 more that had
passed automated checks were rejected when tried on real Windows and macOS
terminals. These counts were read by hand from the team's run log. They are
field observations from private team records, not a controlled with/without
comparison.

## Before And After

Without an evidence discipline:

```text
Claim:    Done — the build is green.
Evidence: Built, but the real runtime was not launched.
```

With Touchstone:

```text
Claim:    Built, not launched.
Evidence: Build evidence only; the runtime check is still owed.
```

## How It Works

1. **Exercise the closest safe reality.** Run and observe the real
   production-shaped environment before relying on narrower checks.
2. **Name the class reached.** Keep inspection, build, seam, runtime, and
   physical evidence from substituting for one another.
3. **Preserve what reality proved.** Add the smallest regression coverage only
   after the real behavior has passed.
4. **Review the literal record.** State what ran, what was observed, what was
   not run, and whether the record is an executor observation, evidence review,
   or independent rerun.

## Guardrails

- Inspection does not prove runtime behavior.
- A green aggregate suite proves only the checks it invoked.
- More proof without a better decision is not progress.
- A human performs only residual checks workers cannot safely execute.
- Touchstone is not a parser, status machine, permission layer, or workflow
  engine.

## Philosophy

Reality is the first test. Evidence is useful only when it supports the claim
being made; a narrower green result does not become stronger by being described
with more confidence.

## Present Boundary

The v1 skill is weighted toward software work: APIs, builds, test seams,
runtimes, devices, and production-shaped environments. Its host-neutral core is
matching a claim to the strongest relevant observation without fabricating a
stronger one. Non-engineering specializations remain future work, not a present
compatibility or efficacy claim.

This public edition matches the v1 skill used inside Current, except that its
literal-history examples name roles instead of internal team members.

## Installation

Install globally for every compatible agent the installer detects:

```sh
npx skills add subcreation/touchstone -g
```

Omit `-g` to install into the current project instead. To list the skill
without installing it:

```sh
npx skills add subcreation/touchstone --list
```

To install from a local clone:

```sh
git clone https://github.com/subcreation/touchstone.git
npx skills add ./touchstone -g
```

## Update

```sh
npx skills update touchstone -g -y
```

For reproducible setups, pin a tagged release instead of following the default
branch, for example:

```sh
npx skills add https://github.com/subcreation/touchstone/tree/v0.1.0 -g
```

## Uninstall

```sh
npx skills remove touchstone -g -y
```

## Compatibility

Touchstone is packaged as a root Agent Skill with optional OpenAI interface
metadata. Before release, the isolated project lifecycle exercise on the
packaging candidate recorded:

| Agent | Packaging evidence |
| --- | --- |
| Codex | The installer copied the candidate root skill into the isolated project. |
| Claude Code | The installer copied the candidate root skill into the isolated project. |

All-agent uninstall left an empty installer registry (`skills-lock.json` with no skills) and no installed skill file in either client path.

These checks concern package placement and lifecycle, not Touchstone behavior or
efficacy. Other Agent Skills clients may discover the root `SKILL.md`, but
remain unverified.

## Troubleshooting

**The claim says works, but only inspection ran.** Return the claim at the
inspection class and name the runtime or physical check still owed.

**The build is green, but the behavior is unknown.** Say built, not launched;
run the closest safe runtime exercise before making a behavior claim.

**A reviewer only read the logs.** Record evidence review, not an independent
rerun.

**A human was asked to repeat a worker-executable check.** Run the safe worker
check first and leave only the genuine residual human observation visible.

## Project

- Read the [roadmap](./ROADMAP.md).
- Inspect or contribute to the [benchmark plan](./benchmarks/README.md).
- Read [CONTRIBUTING.md](./CONTRIBUTING.md) before proposing a behavior change.
- Review the portfolio [art direction](./assets/ART_DIRECTION.md).

Touchstone was built alongside Current, an open-source multi-agent harness
(coming soon).

Touchstone is licensed under the [Apache License 2.0](./LICENSE).
