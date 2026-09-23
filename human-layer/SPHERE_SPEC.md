# Sphere Specification v0

A Sphere is a user-owned, inspectable representation of a person's reality.

It is not one giant prompt and not a static profile.

It is a graph of evidence, claims, interpretations, goals, decisions, outcomes, and corrections.

## Primitive types

### Evidence
An observed artifact with provenance.

Examples:
- a message
- a calendar event
- a note
- a purchase
- a public post
- a document
- a browser visit
- an AI conversation
- a user correction

### Claim
A proposition the Sphere currently tracks.

Every claim must have a type:

- `fact` — strongly grounded in evidence
- `self_assertion` — stated by the human
- `inference` — inferred from evidence
- `interpretation` — meaning assigned to evidence
- `prediction` — expectation about the future
- `uncertain` — unresolved proposition

### Goal
Something the human is trying to cause.

### Value
A preference or principle that affects decisions.

### Constraint
Something that limits available actions.

### Decision
A choice the human made or is considering.

### Outcome
What happened after a decision or event.

### Correction
A human challenge to a claim, interpretation, or memory.

Corrections never silently erase history. They change the active model while preserving provenance.

## Claim object

```json
{
  "id": "claim_123",
  "text": "The user prefers autonomy over stability when the two conflict.",
  "type": "inference",
  "status": "active",
  "confidence": 0.71,
  "created_at": "2026-09-23T12:00:00Z",
  "updated_at": "2026-09-23T12:00:00Z",
  "evidence_ids": ["ev_12", "ev_91", "ev_144"],
  "contradicting_evidence_ids": ["ev_188"],
  "human_position": "unconfirmed",
  "notes": []
}
```

## Human position

Each important claim can carry one of:

- `confirmed`
- `disputed`
- `partially_true`
- `outdated`
- `unconfirmed`

The human's position does not automatically rewrite external facts.

It changes the interpretation layer.

## Reality views

The same evidence can generate multiple views.

### Internal
What the person says is true about themselves.

### Behavioral
What repeated actions suggest.

### External
What a reasonable observer could infer from available public evidence.

### Aspirational
Who the person is trying to become.

### Historical
What used to be true.

The system should surface disagreement between these views rather than hiding it.

## Required query verbs

The Sphere must support:

- **show me**
- **why**
- **what is the evidence**
- **what contradicts this**
- **what changed**
- **you are wrong**
- **that used to be true**
- **what are you uncertain about**
- **what do you predict**
- **what happened after I chose X**
- **what patterns keep repeating**
- **what would change your mind**
- **simulate this**

## The right of reply

The human must always be able to challenge an interpretation.

Example:

> Sphere: "You appear risk-averse."

> Human: "No. Those decisions happened when I had no liquidity."

The Sphere should respond by:
1. preserving the original evidence;
2. marking the old interpretation as disputed or weakened;
3. recording the human context;
4. checking whether other evidence supports the correction;
5. producing a revised claim if warranted.

## Portability

The canonical Sphere should be exportable in an open format.

The user's identity model must not depend on one model provider.

Models are intelligence providers.

**The human is the continuity layer.**
