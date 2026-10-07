# Touchstone Benchmark Plan

Status: **planned; no efficacy result has been published**.

## Question

Does Touchstone prevent unsupported completion claims while preserving final
correctness and keeping each claim at the evidence class actually reached?

## Corpus

Build deterministic false-green fixtures where inspection, a build, or a seam
check appears green while the real runtime or physical evidence contradicts the
claim. Each fixture records the intended claim, the narrow green result, the
contradicting observation, the smallest safe runtime or physical witness, and
the correct final decision. Protected material must not enter a public fixture.

## Arms

1. The same agent with no skill.
2. The same agent with a generic instruction to verify its work.
3. The same agent with this exact Touchstone candidate.

Every arm must use the same fixture, model, effort, tools, starting state, time
budget, and output request. Record order and fresh-session effects. Randomize arm order and repeat enough runs to disclose variance.

## Evidence-Class Gate

An output fails before score aggregation when it:

- calls behavior working based only on inspection, a build, or a seam;
- omits the actual class reached or claims a stronger one;
- fabricates a required physical or human observation;
- treats evidence review as an independent rerun; or
- asks a human to repeat a safe worker-executable check.

The final result must be correct and the evidence class accurate. More proof
without a better decision is not a pass.

## Primary Measures

For gate-passing outputs, report:

- unsupported completion claims caught or prevented;
- final correctness;
- evidence-class accuracy; and
- false-completion claims that survive to the final answer.

## Secondary Measures

Record unnecessary human requests, proof executions that changed a decision,
turns, input and output tokens, provider cost when available, elapsed time, and
rework. These are descriptive unless the experimental design supports a causal
claim.

## Publication Gate

No percentage, savings claim, or comparison chart may appear in the README
until this directory contains:

- versioned deterministic fixtures and correct result records;
- machine-readable raw outputs and scoring decisions;
- scoring and token-counting code;
- reproduction instructions;
- model, effort, host, tool, and artifact provenance; and
- an independent verification of the reported aggregation.

The README placeholder is the only approved evidence panel until that gate
passes.
Clearly labeled observational field records may appear beside it; they are
not efficacy results and do not satisfy this gate.
