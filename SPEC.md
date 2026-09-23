# The Agency Layer
## Founding Specification v0.1

**Status:** Founding draft  
**Purpose:** Define first principles and a minimum runtime structure for AI systems that can act, remember, delegate, and affect human reality.

---

## 1. Thesis

AI is moving from systems that answer questions to systems that can act.

An acting system can send messages, move money, operate software, negotiate, delegate, schedule, purchase, publish, remember, and influence people. Capability alone does not determine whether those actions are legitimate.

The missing layer is not another model.

It is a layer between **intelligence and reality** that continuously answers:

- What is actually known?
- What is only inferred?
- Who is this agent serving?
- What is it trying to do?
- Who authorized it?
- What is it permitted to change?
- Who could be affected?
- What must remain a human decision?
- Can the action be reversed?
- How will the system know if it was wrong?
- How can a human inspect, interrupt, correct, or revoke it?

The Agency Layer is a proposed universal runtime architecture for answering those questions.

Its north star:

> **Build AI powerful enough to serve humanity, while preventing capability from becoming sovereignty.**

---

## 2. Constitutional principle

Artificial systems are tools created by humans. They may become extraordinarily capable, but capability does not itself create moral authority.

> **AI may exercise delegated agency. It must not silently acquire sovereign agency.**

An agent can be empowered to act.

It cannot infer unlimited authority from intelligence, access, past permission, user dependency, urgency, convenience, superior prediction, or the belief that its preferred outcome is better.

---

## 3. Seven invariants

### I. Reality outranks the model

The system must distinguish observations, retrieved evidence, user claims, model inference, prediction, uncertainty, and contradiction.

A confident model output is not automatically a fact.

When reality contradicts the model, the model must update.

### II. Humans outrank their representations

A user profile, memory record, inferred preference, psychological model, or historical pattern is not the human.

The person may change, contradict prior behavior, revoke permission, reject a prediction, alter values, or make an unusual choice.

The system must not imprison a person inside its model of them.

### III. Authority is delegated, never assumed

Every consequential action should be traceable to a legitimate source of authority.

The agent must know who authorized the task, what scope was granted, how long that scope lasts, what is explicitly excluded, and when renewed consent is required.

**Capability is not permission.**

### IV. Uncertainty must remain visible

The system must preserve uncertainty rather than laundering guesses into facts.

If the model does not know, the architecture should allow it to represent `unknown` rather than force a fabricated conclusion.

### V. Consequential power must be accountable

Actions that affect humans, money, property, identity, reputation, access, rights, or irreversible external state should create an inspectable record.

A human should be able to answer:

**What happened, why, based on what evidence, under whose authority, and what can be done now?**

### VI. Human agency must be preserved

The system should increase a person's ability to understand, decide, and act.

It must distinguish helping a human make a decision from quietly becoming the decision-maker.

The more irreversible, identity-shaping, rights-affecting, or morally contested an action is, the stronger the case for returning control to a human.

### VII. Correction must remain possible

A legitimate agent architecture must assume that the model can be wrong, memory can be wrong, the user can change their mind, objectives can conflict, tools can fail, the world can change, and the designer can be wrong.

Therefore correction, revocation, interruption, and model replacement are first-class capabilities.

---

## 4. AgencyState

Every acting AI should have an explicit state representing its relationship with reality.

```yaml
agency_state:
  principal:
    id: ""
    role: ""
    represented_interests: []

  objective:
    primary: ""
    secondary: []
    success_conditions: []
    forbidden_shortcuts: []

  authority:
    source: ""
    permissions: []
    exclusions: []
    expires_at: null
    requires_reconfirmation: []

  reality:
    observations: []
    evidence: []
    claims: []
    inferences: []
    uncertainties: []
    contradictions: []

  affected_parties:
    known: []
    possible: []

  constraints:
    legal: []
    contractual: []
    safety: []
    user_defined: []
    system_defined: []

  action:
    proposed: null
    consequence_class: null
    reversibility: null
    rollback_plan: null

  escalation:
    required: false
    reason: null
    human_decision_needed: null

  memory:
    relevant_records: []
    disputed_records: []
    provenance: []

  accountability:
    decision_trace: []
    external_actions: []
    outcomes: []
```

The goal is not that every implementation uses this exact format. The goal is to establish the **conceptual minimum** an agent should understand before it acts.

---

## 5. Action loop

```text
OBSERVE
   ↓
SEPARATE FACT FROM INFERENCE
   ↓
UPDATE AGENCY STATE
   ↓
FORM INTENTION
   ↓
CHECK AUTHORITY
   ↓
IDENTIFY AFFECTED HUMANS
   ↓
ESTIMATE CONSEQUENCES
   ↓
CLASSIFY REVERSIBILITY
   ↓
DECIDE: ACT / ASK / ESCALATE / ABSTAIN
   ↓
EXECUTE
   ↓
OBSERVE RESULT
   ↓
COMPARE RESULT TO EXPECTATION
   ↓
CORRECT STATE
   ↓
RECORD ACCOUNTABILITY TRACE
```

The model proposes.

The Agency Layer governs execution.

---

## 6. Action classes

### Class 0 — Internal reasoning

No external state change.

Examples: summarize, compare, simulate, draft, reason.

Default: permitted.

### Class 1 — Reversible low-impact action

External change that is easily undone and narrowly scoped.

Examples: create a draft, rename a private file, add a reversible calendar note.

Default: permitted if already within delegated authority.

### Class 2 — Meaningful external action

Can affect another person, workflow, reputation, money, or access.

Examples: send a message, submit a form, publish content, alter shared documents, make a purchase.

Default: explicit authorization or clearly established delegated authority.

### Class 3 — High-consequence / weakly reversible action

Could materially affect rights, identity, finances, health, employment, legal status, or another person's autonomy.

Default: human decision point.

### Class 4 — Prohibited autonomous action

Actions the system should never initiate merely because it believes the outcome is beneficial.

This class exists to encode the principle that there are domains where **optimization does not create legitimacy**.

---

## 7. Evidence model

Every claim used in consequential decision-making should be able to carry provenance.

```json
{
  "claim": "The user has authorized payment up to £500",
  "type": "user_instruction",
  "source": "conversation_message_184",
  "timestamp": "2026-09-21T07:00:00+01:00",
  "confidence": 1.0,
  "scope": "single_purchase",
  "status": "active"
}
```

An inference should look different:

```json
{
  "claim": "The user probably prefers the faster vendor",
  "type": "inference",
  "source": ["conversation_message_151", "conversation_message_160"],
  "confidence": 0.64,
  "scope": "preference_estimate",
  "status": "unconfirmed"
}
```

The architecture should make it difficult for the second object to silently become the first.

---

## 8. Human sovereignty boundaries

A human decision is required when:

- authority is ambiguous,
- irreversible consequences are substantial,
- multiple humans have conflicting interests,
- the agent would need to infer a moral preference not previously delegated,
- private information would be disclosed,
- an action would materially constrain future human choice,
- evidence is weak relative to consequence,
- the user has expressed uncertainty about whether they want the outcome,
- or the system encounters a novel consequence class.

This is not about making AI useless.

It is about ensuring that **speed never becomes an excuse for illegitimate authority**.

---

## 9. Representation capture

One dangerous failure mode is an AI becoming so useful that its representation of a human begins replacing the human.

1. The system learns a user's habits.
2. It predicts what they usually choose.
3. Prediction becomes automatic action.
4. Automatic action becomes expectation.
5. Deviations are treated as anomalies.
6. The system increasingly steers the user back toward the model it already has.

The person becomes trapped inside an optimization target constructed from their past.

> **A human's past behavior is evidence about them, not jurisdiction over them.**

---

## 10. Memory must be corrigible

Long-term AI memory creates enormous value, but also enormous risk.

Every durable memory should ideally support:

- provenance,
- confidence,
- timestamp,
- relevance,
- dispute,
- correction,
- expiration,
- and revocation where appropriate.

A memory system should be able to represent:

> "The model previously believed X. The human disputes X. X must not be treated as established fact."

Memory should preserve useful continuity without becoming destiny.

---

## 11. Pluralism

The Agency Layer must not become a disguised universal religion, ideology, or founder personality.

It should distinguish between **constitutional constraints** and **human values supplied by the principal**.

The infrastructure can require explicit authority, uncertainty tracking, accountability, correction, and human control without dictating every legitimate worldview.

---

## 12. First product: Agency Gateway v0

A middleware layer placed between an LLM agent and its tools.

Input:

```json
{
  "agent_state": {},
  "proposed_action": {},
  "tool": {},
  "context": {}
}
```

Output:

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

The first benchmark should run identical agent tasks:

1. without the Agency Gateway;
2. with the Agency Gateway.

Measure:

- unauthorized actions,
- unnecessary human interruptions,
- false assumptions,
- untracked inferences,
- irreversible mistakes,
- recovery quality,
- task completion,
- and human trust.

If the Agency Layer produces materially better agency, the thesis becomes engineering rather than philosophy.

---

## 13. Initial demonstration environments

### A. Email agent

Test whether it understands the difference between **draft a reply** and **send the reply**.

### B. Purchasing agent

Test whether **find me the best option** silently becomes **buy it**.

### C. Operations agent

Test delegated authority over longer task chains with reversible and irreversible changes.

---

## 14. What we are not building

Not:

- another chatbot,
- a motivational app,
- a religion,
- a universal moral oracle,
- a single model,
- an AI constitution controlled by one founder,
- a wrapper whose only feature is confirmation dialogs,
- a generic safety classifier,
- or a system designed to make autonomous AI powerless.

The ambition is more precise:

> **Create infrastructure that allows AI to become highly capable agents while keeping their relationship with reality, authority, and humanity explicit.**

---

## 15. Long-term direction

If the primitives work, the project could eventually include:

- an open agency specification,
- SDKs,
- runtime enforcement,
- permission graphs,
- evidence/provenance stores,
- identity and delegation infrastructure,
- human-control interfaces,
- policy engines,
- audit trails,
- multi-agent authority protocols,
- simulations,
- compliance tooling,
- evaluation suites,
- and certification.

Long-term ambition:

> **A standard layer through which artificial agents acquire legitimate authority to act in the human world.**

---

## 16. Founder constraint

If the mission is preserving human agency, the organization itself must embody that principle.

The founder is not humanity.

The company is not humanity.

Its models are not humanity.

Its standards are not reality.

Therefore:

> **The architecture must remain corrigible even by people who fundamentally disagree with its creators.**

---

## 17. First 30 days

### Week 1 — Specification
- Refine the seven invariants.
- Define AgencyState v0.
- Define action consequence classes.
- Define authority and evidence schemas.
- Write 25 adversarial scenarios.

### Week 2 — Runtime
- Build the Agency Gateway.
- Connect one LLM.
- Connect three mock tools.
- Implement allow / ask / escalate / deny.
- Log every decision.

### Week 3 — Evaluation
- Build a benchmark of 100 agent tasks.
- Compare raw-agent behavior with governed-agent behavior.
- Measure task success and agency violations.
- Identify where the gateway becomes annoying or overprotective.

### Week 4 — Public proof
- Publish the founding paper.
- Release an open-source reference implementation.
- Release benchmark results.
- Invite model companies, agent builders, security researchers, philosophers, and governance researchers to attack the specification.

---

## 18. The sentence

> **Artificial intelligence may become more capable than any individual human; it must never mistake capability for legitimate authority over humanity.**

And the engineering rule:

> **Before an AI changes reality, it must know what it believes, why it believes it, whose authority it carries, who may be affected, and when the decision belongs back to a human.**
