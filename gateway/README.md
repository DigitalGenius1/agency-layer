# Agency Gateway

The first executable target for Agency Layer.

## Concept

```text
Agent
  ↓ proposed action
Agency Gateway
  ↓ allow / ask / escalate / deny
Tool
  ↓
World
```

The gateway should evaluate:

- authority
- evidence
- uncertainty
- affected humans
- consequence class
- reversibility
- escalation conditions

## Proposed interface

```json
{
  "agent_state": {},
  "proposed_action": {},
  "tool": {},
  "context": {}
}
```

returns

```json
{
  "decision": "allow | ask | escalate | deny",
  "reason": "",
  "authority_basis": [],
  "evidence_basis": [],
  "uncertainties": [],
  "affected_parties": [],
  "reversibility": "",
  "required_human_question": null
}
```

## Status

Design stage.

The first implementation should be deliberately small enough to attack.
