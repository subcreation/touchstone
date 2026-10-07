---
name: touchstone
description: Reality-first proof discipline for any claim that software works. Use whenever work is about to be called done, working, verified, or ready for review - and whenever reviewing such a claim. Reality is the first test; regression coverage preserves what reality proved.
---

# Touchstone

A claim that software works is a claim about reality, and reality is the
first test the software must pass. Run the real thing before calling it
done; cover it with tests after it is known to work, so regressions are
caught quickly and cheaply.

## The order

1. Solve the real problem in reality first: the closest safe, faithful,
   production-shaped environment you can reach from where you work - the
   real API shape, the real device or platform, the real deployment
   configuration. Safe means safe: never unrestricted testing against live
   production services, customer data, or irreversible operations without
   explicit authorization.
2. Confirm the behavior by running it and observing the result - not by
   reading the code, not by compiling it, not by imagining the run.
3. Only after reality has passed, add the smallest regression coverage that
   would fail if the proven behavior broke: integration coverage first,
   unit coverage after, UI checks where the visible surface is the product.

Tests preserve what reality proved. Tests written for unproven code enshrine
a guess in the wrong shape and force rework once reality disagrees. One
shape of failing-test-first remains reality-first: when a real failure has
been observed, freezing it as a RED regression check before the fix
preserves an observation. What this order forbids is enshrining guesses
about behavior never observed.

## Evidence classes

Evidence types are not interchangeable. Each proves only what it exercised:

- **Inspection** - reading source, diffs, or strings in a binary - proves
  structure.
- **A build** proves compilation.
- **A seam test** - a unit, API, or contract test, possibly against stubs -
  proves the seam it ran, not the screen and not the deployed runtime.
- **A runtime run** - launching the real artifact against its real
  counterpart - proves only the behavior actually exercised and observed
  in that run.
- **Physical experience** - a human on the real device in real conditions -
  proves only what was actually observed.

A claim names its evidence class and never exceeds it. "Works" backed by
inspection is a false claim, not a shortcut. A successful build is not
behavior. A green seam test against a stub says nothing about what a user
sees.

## Claims and handoffs

Every done, working, or ready claim states:

- exactly what was run: commands, environment, endpoints, versions;
- what was observed: output, logs, screenshots - artifacts, not adjectives;
- what was not run, and why;
- for each acceptance item, the honest evidence class. A behavioral
  acceptance item requires runtime evidence of that particular behavior -
  a run that exercised something else does not cover it.

When authoring acceptance criteria, name the evidence class each item
requires and who can produce it; an item that describes behavior but names
no executor invites evidence substitution.

If you cannot reach the real environment, say so and return the work as
blocked on that proof, at the class you actually reached. Relabeling
inspection as behavior ("verified in source") is the exact failure this
discipline exists to prevent. An unreachable dependency rarely excuses not
running at all: an app launched against a dead server still proves launch,
configuration, security policy, and failure behavior - and often reveals
the defect that inspection cannot see.

## Reviewing a claim

The reviewer reviews the evidence class, not just the pass or fail:

- Accept each claim only at the class of its evidence. A behavioral claim
  carrying inspection or build evidence returns to the implementer as a
  finding; the reviewer never upgrades it.
- If you cannot execute a check yourself, require the evidence from whoever
  can. Being unable to run it transfers the run - it never waives it.
- Keep three things distinct in what you record: **executor observation**
  (the implementer ran it and observed), **evidence review** (you opened
  the artifacts but could not rerun), and **independent rerun** (someone
  else executed the same check). Only an independent rerun is independent
  verification; evidence review is recorded as evidence review, never as
  verification.
- A fallback, subset, or partial delivery is accepted as exactly that,
  never as the full requirement.
- Do not accept from summary alone; open the evidence.
- A green aggregate suite proves only the checks it actually invoked. For every
  regression witness the work's requirements name as preserved, verify that
  its command actually ran in this candidate. A proof file that merely exists,
  a skipped check, or a witness omitted from the suite is no evidence.
- A resolved real-world failure that shares the changed production seam is a
  mandatory regression control. Run its retained proof independently before
  accepting the new behavior. A proof that crashes, cannot reach its assertion,
  or returns a different terminal shape is red, even when another suite is
  green.

## The human's place

A human verifier receives only the residual checks the organization cannot
execute itself: physical devices, real accounts, live external conditions,
experiential judgment. The human must never be asked to be the first to run
behavior a worker could have run; a human who chooses to test early does so
freely, but the organization may not depend on it. Before a human spends a
real-world test, every worker-executable check that could catch known
failure classes has already passed.

Every human-verification handoff names the exact repository, commit, local
project path, and literal setup and launch commands, with no placeholders. It
also states what to observe and which acceptance items the human is checking.
The commands must run as written from the named fresh shell: establish every
required credential/environment value and use the supported interpreter rather
than relying on ambient activation, inherited variables, or a command known to
be absent on that host.

## Say what happened, literally

Do not invent a status vocabulary. State claims as literal history: "not
run", "built, not launched", "run by the implementer on macOS against the
live server", "evidence reviewed by the owner", "independently rerun by a
second reviewer". A
reader must be able to tell from the words alone what physically happened
and who did it. Completion language belongs to the organization's review,
not to the implementer's claim.

## Boundaries

Touchstone defines what evidence justifies a claim. It does not decide how
small the code should be (a simplicity discipline owns that), how work is
committed and handed off (Git hygiene owns that), how to investigate a
surprise once one exists (evidence-led investigation owns that), or what to
build (requirements work owns that). A minimal self-check written under a
simplicity discipline preserves a behavior already proven in reality; it
never substitutes for running the real thing. Touchstone is a discipline
for people and reviewers - never a parser, a status machine, a token
grammar, a status vocabulary of its own, or an automated gate.
