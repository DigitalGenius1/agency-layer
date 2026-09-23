# Agency Layer

**Open research and infrastructure for legitimate AI agency in the human world.**

> **Capability does not create legitimate authority.**

AI systems are becoming able to do more than answer questions. They can use tools, remember context, delegate work, change external state, and act over longer time horizons.

Agency Layer is a public research lab exploring a basic question:

## As AI gains the ability to act, what gives it legitimate authority to change the human world?

We are developing and testing primitives for:

- **Authority** — who authorized the action, and within what scope?
- **Evidence** — what is observed, claimed, inferred, predicted, or unknown?
- **Human agency** — which decisions must remain with people?
- **Memory** — how should persistent representations remain correctable?
- **Reversibility** — how should autonomy change with consequence?
- **Accountability** — can we reconstruct what happened and why?
- **Correction** — can people interrupt, revoke, dispute, or update the system?

## Working principles

1. **Reality outranks the model.**
2. **Humans outrank their representations.**
3. **Authority is delegated, never assumed.**
4. **Uncertainty must remain visible.**
5. **Consequential power must be accountable.**
6. **Human agency must be preserved.**
7. **Correction must remain possible.**

These are hypotheses to test, not commandments to protect.

## The research loop

```text
problem
  ↓
proposal
  ↓
experiment
  ↓
criticism
  ↓
revision
  ↓
better proposal
```

If an assumption fails, we change it.

**Reality outranks this project too.**

## Current work

- [SPEC.md](./SPEC.md) — founding specification v0.1
- [PRINCIPLES.md](./PRINCIPLES.md) — constitutional invariants
- [experiments/001-ambiguous-delegation.md](./experiments/001-ambiguous-delegation.md) — first benchmark concept
- [examples/agency-state.yaml](./examples/agency-state.yaml) — proposed state representation
- [objections/README.md](./objections/README.md) — how criticism becomes part of the architecture
- [gateway/README.md](./gateway/README.md) — first executable target
- [CONTRIBUTING.md](./CONTRIBUTING.md) — how to attack or improve the work
- [CHANGELOG.md](./CHANGELOG.md) — what changed and why

## What this is not

Agency Layer is not:

- a universal moral oracle
- a religion or ideology for AI
- a claim that one founder should decide what humanity wants
- a generic confirmation-dialog wrapper
- an attempt to make useful agents powerless
- a finished standard

The ambition is narrower and more demanding:

> **Allow AI systems to become highly capable while keeping their relationship with reality, authority, and human choice explicit.**

## Public invitation

Do not agree with this project by default.

Tell us:

- what is already solved better elsewhere
- what is technically impossible
- what is dangerously underspecified
- which primitive is unnecessary
- what breaks under multi-agent or multi-human systems
- where human approval becomes useless friction
- where the proposed architecture still allows illegitimate authority

Open an issue. Bring evidence. Break the model.

## Status

**v0.1 — founding research phase**

The first goal is not market ownership.

The first goal is to **understand and own the problem well enough that serious builders can test the proposed abstractions against reality.**
