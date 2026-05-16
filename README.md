# Contribution Tolerance Band Model

Contribution Tolerance Band Model defines contribution not as a single exact value, but as an interval-based estimate with an explainable tolerance band.

It is designed for royalty allocation, trace evaluation, attribution systems, and dispute-resistant value distribution under imperfect evidence.

---

## One-Line Definition

Contribution Tolerance Band Model v0.1 is an uncertainty-aware contribution assessment model that represents contribution as a range rather than a fixed point.

Instead of asking:

> “Who contributed exactly 47%?”

this model asks:

> “Within what explainable range can this contribution be fairly assessed?”

---

## Why This Exists

In AI-mediated creation, protocol design, writing, software development, research, and trace-based royalty systems, contribution is often difficult to measure precisely.

A contribution may appear as:

- an original question
- a structural idea
- a protocol design
- an implementation
- an edit
- a transformation
- an indirect influence
- a long-term trace
- a disputed or partially visible lineage

Because of this, exact contribution scoring can create false precision.

For example:

```text
Contributor A: 47%
Contributor B: 38%
Contributor C: 15%
```

This looks precise, but the evidence may not justify that level of certainty.

Contribution Tolerance Band Model avoids false precision by using tolerance bands.

```text
Contribution Range = estimated_value ± tolerance_band
```

Example:

```text
Contributor A: 42% - 50%
Contributor B: 35% - 43%
Contributor C: 12% - 18%
```

The purpose is not to eliminate uncertainty.

The purpose is to make uncertainty visible, bounded, explainable, and governable.

---

## Core Concept

Contribution should not be treated as a fixed point.

It should be treated as a flexible but auditable range.

```text
C = μ ± ε
```

Where:

- `C` = contribution range
- `μ` = estimated contribution value
- `ε` = tolerance band
- `μ - ε` = lower bound
- `μ + ε` = upper bound

Example:

```json
{
  "contributor_id": "contributor_A",
  "estimated_value": 0.46,
  "tolerance_band": 0.04,
  "range": {
    "lower_bound": 0.42,
    "upper_bound": 0.50
  }
}
```

A narrow band means stronger evidence and higher confidence.

A wide band means greater uncertainty and may trigger review, pooled allocation, deferred allocation, or dispute handling.

---

## Core Principle

Do not force exactness where exactness cannot be justified.

This model does not claim to calculate the absolute truth of contribution.

Instead, it provides a structured way to estimate contribution under uncertainty.

The central principle is:

> Make uncertainty visible, bounded, explainable, and governable.

---

## Good Uncertainty vs Bad Ambiguity

This model distinguishes between controlled uncertainty and uncontrolled ambiguity.

### Good Uncertainty

Good uncertainty is explainable.

It may come from:

- incomplete but meaningful evidence
- partial structural similarity
- moderate trace confidence
- estimator disagreement within acceptable limits
- indirect but plausible influence

Example:

```text
Contributor A: 42% - 50%
```

This is acceptable if the band width is justified.

### Bad Ambiguity

Bad ambiguity is too broad to support safe allocation.

Example:

```text
Contributor A: 10% - 90%
```

This should not be used for automatic allocation.

It should trigger review, dispute handling, deferred allocation, or shared pool handling.

---

## Model Structure

A Contribution Tolerance Band assessment may include:

- contribution assessment metadata
- target work information
- contributor assessments
- estimated values
- tolerance bands
- contribution ranges
- evidence bundles
- estimator outputs
- uncertainty factors
- contribution layers
- allocation recommendations
- review triggers
- governance metadata
- relationships to other trace or royalty systems

---

## Contribution Layers

For human readability, contribution may also be expressed as layers.

Instead of relying only on numbers, the model can classify contributors as:

```text
Primary Contribution Layer
Near Contribution Layer
Supporting Contribution Layer
Shared Influence Layer
Unresolved / Disputed Layer
```

This reduces unnecessary conflict caused by excessive numerical precision.

Example:

```json
{
  "primary_contribution_layer": ["contributor_A"],
  "near_contribution_layer": ["contributor_B"],
  "supporting_contribution_layer": ["contributor_C"],
  "shared_influence_layer": ["contributor_D"],
  "unresolved_layer": []
}
```

---

## Allocation Behavior

Contribution Tolerance Band Model does not directly enforce payment.

It provides allocation guidance.

Possible allocation outcomes include:

```text
automatic_allocation
pooled_allocation
equalized_allocation
human_review
dispute_registry
deferred_allocation
common_culture_pool
no_allocation
```

### Automatic Allocation

Used when:

- evidence is strong
- tolerance bands are narrow
- estimator agreement is high
- dispute risk is low

### Pooled Allocation

Used when:

- contributor ranges overlap
- contributions are difficult to separate
- influence is shared
- strict ranking would create unnecessary conflict

### Human Review

Used when:

- tolerance bands are too wide
- evidence is conflicting
- estimator agreement is low
- high-value distribution is involved

### Common Culture Pool

Used when:

- influence may be real but not individually attributable
- origin is unclear
- contribution has become broadly cultural
- evidence is too weak for individual allocation

---

## Yin-Yang Balance Interpretation

This model may be interpreted as a Yin-Yang balance system.

### Yang Evidence

Yang represents visible, explicit, externalized evidence.

Examples:

- citation
- signature
- timestamp
- code commit
- publication history
- explicit reference
- repository history
- C2PA-style provenance
- signed attestation

### Yin Influence

Yin represents hidden, structural, indirect, or long-term influence.

Examples:

- conceptual resonance
- structural similarity
- origin-question influence
- implicit inspiration
- design lineage
- cultural diffusion
- long-term transformation

A healthy contribution model should not rely only on Yang evidence.

It should also recognize Yin influence.

However, it should not rely only on Yin influence either.

Unverified influence claims must not automatically generate strong allocation rights.

Therefore, this model seeks a middle balance.

```text
Too much Yang  → only explicit records matter
Too much Yin   → vague influence claims dominate
Middle Balance → evidence and structure are both considered
```

This is the willow model of allocation:

> flexible enough to bend with uncertainty,  
> rooted enough to remain auditable.

---

## Repository Structure

```text
contribution-tolerance-band-model/
├─ .github/
│  └─ workflows/
│     └─ validate-specs.yml
├─ docs/
│  ├─ contribution-tolerance-band-model.md
│  ├─ relationship-to-royalty-os.md
│  ├─ relationship-to-ksd.md
│  ├─ relationship-to-trace-protocol.md
│  ├─ relationship-to-dispute-registry.md
│  ├─ allocation-readiness.md
│  ├─ review-status-notes.md
│  └─ governance-bridge-notes.md
├─ examples/
│  └─ contribution-tolerance-band.sample.json
├─ schemas/
│  └─ contribution-tolerance-band-v0.1.schema.json
├─ LICENSE
└─ README.md
```

---

## Start Here

- [`docs/contribution-tolerance-band-model.md`](docs/contribution-tolerance-band-model.md)  
  Main explanatory document for the Contribution Tolerance Band Model.

- [`schemas/contribution-tolerance-band-v0.1.schema.json`](schemas/contribution-tolerance-band-v0.1.schema.json)  
  JSON Schema for validating Contribution Tolerance Band records.

- [`examples/contribution-tolerance-band.sample.json`](examples/contribution-tolerance-band.sample.json)  
  Example record showing interval-based contribution assessment.

- [`.github/workflows/validate-specs.yml`](.github/workflows/validate-specs.yml)  
  GitHub Actions workflow for validating schema compliance and numerical consistency.

---

## Related Documents

- [`docs/relationship-to-royalty-os.md`](docs/relationship-to-royalty-os.md)  
  Explains how this model serves as the uncertainty-aware contribution layer for Royalty OS.

- [`docs/relationship-to-ksd.md`](docs/relationship-to-ksd.md)  
  Explains how KSD and Structure Fingerprint provide structural evidence for contribution assessment.

- [`docs/relationship-to-trace-protocol.md`](docs/relationship-to-trace-protocol.md)  
  Explains how Trace Protocol records become trace evidence for contribution ranges.

- [`docs/relationship-to-dispute-registry.md`](docs/relationship-to-dispute-registry.md)  
  Explains how disputed or contested contribution assessments should be governed.

- [`docs/allocation-readiness.md`](docs/allocation-readiness.md)  
  Defines when a contribution assessment is stable enough to influence allocation.

- [`docs/review-status-notes.md`](docs/review-status-notes.md)  
  Explains assessment lifecycle states, review reasons, and review transitions.

- [`docs/governance-bridge-notes.md`](docs/governance-bridge-notes.md)  
  Connects assessment, review, readiness, dispute handling, and Royalty OS allocation policy.

---

## Schema Usage

This repository uses JSON Schema Draft 2020-12.

The main schema is located at:

```text
schemas/contribution-tolerance-band-v0.1.schema.json
```

The example file is located at:

```text
examples/contribution-tolerance-band.sample.json
```

The schema validates the structure of a Contribution Tolerance Band assessment, including:

- required metadata
- contributor records
- contribution ranges
- evidence bundles
- estimator outputs
- allocation recommendations
- governance metadata
- relationship records

---

## Validation

This repository includes a GitHub Actions workflow:

```text
.github/workflows/validate-specs.yml
```

The workflow performs both JSON Schema validation and additional custom consistency checks.

### JSON Schema Validation

The workflow validates:

- schema compliance
- required fields
- allowed enum values
- object structure
- value ranges
- URI and date-time formats

### Custom Numerical Validation

The workflow also checks numerical consistency that JSON Schema alone cannot fully enforce.

It validates:

```text
lower_bound <= upper_bound
lower_bound = estimated_value - tolerance_band
upper_bound = estimated_value + tolerance_band
allocation_share total = 1.0
shared_pool_policy.pool_share consistency
review_required / review_reasons consistency
```

This prevents invalid contribution ranges from passing validation.

---

## Example

Minimal contributor range example:

```json
{
  "contributor_id": "contributor_A",
  "estimated_value": 0.46,
  "tolerance_band": 0.04,
  "range": {
    "lower_bound": 0.42,
    "upper_bound": 0.50
  },
  "confidence": 0.82,
  "evidence_strength": 0.78,
  "trace_confidence": 0.74,
  "estimator_agreement": 0.81,
  "dispute_risk": 0.12,
  "contribution_layer": "primary"
}
```

This means the contributor is not treated as having exactly `46%`.

Instead, the contributor is assessed within an explainable range:

```text
42% - 50%
```

---

## Review Triggers

A contribution assessment may require review when:

```text
tolerance_band is too wide
evidence_strength is too low
trace_confidence is too low
estimator_agreement is too low
dispute_risk is too high
ranges overlap in a conflict-sensitive way
counter-evidence exists
high-value distribution is involved
manual review is requested
```

When review is required, allocation may be:

- deferred
- pooled
- sent to human review
- sent to dispute handling
- placed into a shared influence pool
- placed into a common culture pool

---

## Relationship to Royalty OS

Contribution Tolerance Band Model can serve as an uncertainty-aware contribution layer for Royalty OS and trace-based allocation systems.

Royalty OS may use this model to determine whether a contribution case should result in:

- automatic allocation
- pooled allocation
- equalized allocation
- human review
- dispute registry handling
- deferred allocation
- common culture pool allocation

This model does not replace Royalty OS.

It strengthens Royalty OS by preventing false precision in contribution scoring.

See also: [`docs/relationship-to-royalty-os.md`](docs/relationship-to-royalty-os.md)

---

## Relationship to KSD / Structure Fingerprint

KSD and Structure Fingerprint provide structural evidence.

They help determine:

- whether two works share structural lineage
- whether a question, pattern, or architecture has been inherited
- whether similarity is superficial or structural
- whether indirect influence may exist

Contribution Tolerance Band Model uses this evidence to adjust the tolerance band.

Strong structural evidence narrows uncertainty.

Weak or ambiguous structural evidence widens uncertainty.

See also: [`docs/relationship-to-ksd.md`](docs/relationship-to-ksd.md)

---

## Relationship to Trace Protocol

Trace Protocol provides trace paths.

These may include:

- access trace
- influence trace
- audit trace
- reference trace
- transformation trace

Contribution Tolerance Band Model uses trace confidence to determine whether the contribution range should be narrow or wide.

Clear trace paths generally narrow the tolerance band.

Missing, indirect, or disputed trace paths generally widen the tolerance band.

See also: [`docs/relationship-to-trace-protocol.md`](docs/relationship-to-trace-protocol.md)

---

## Relationship to Signed Impact Attestation

Signed Impact Attestation provides accountable claims.

If an evaluator, institution, or reviewer claims that a contributor had a certain impact, that claim can be included as evidence.

However, a signed claim does not automatically determine final contribution.

It may affect:

- evidence strength
- dispute risk
- estimator confidence
- review status

---

## Relationship to Dispute Registry

If a contribution estimate is challenged, the case may be sent to Dispute Registry.

Dispute Registry may record:

- objection
- correction
- supersession
- revocation
- reaffirmation
- review outcome

Contribution Tolerance Band Model should not hide disputes.

It should make uncertain or contested contribution visible.

See also: [`docs/relationship-to-dispute-registry.md`](docs/relationship-to-dispute-registry.md)

---

## Allocation Readiness

Allocation Readiness defines when a Contribution Tolerance Band assessment is sufficiently stable to influence allocation.

A contribution assessment should not automatically become an allocation decision.

It must pass a readiness gate based on:

- tolerance band width
- evidence strength
- trace confidence
- estimator agreement
- dispute risk
- review status
- value at risk

See also: [`docs/allocation-readiness.md`](docs/allocation-readiness.md)

---

## Review Status

Review Status defines how contribution assessments express lifecycle state and review requirements.

An assessment may be:

```text
draft
active
review_required
disputed
superseded
revoked
archived
```

Review status prevents unstable assessments from being mistaken for final decisions.

See also: [`docs/review-status-notes.md`](docs/review-status-notes.md)

---

## Governance Bridge

Governance Bridge connects assessment, review, allocation readiness, dispute handling, and Royalty OS allocation policy.

Its core rule is:

> A contribution range should never become an allocation decision without governance.

See also: [`docs/governance-bridge-notes.md`](docs/governance-bridge-notes.md)

---

## Non-Goals

This model does not:

- determine legal ownership
- replace copyright law
- prove absolute originality
- guarantee perfect fairness
- calculate the metaphysical truth of influence
- enforce payment by itself
- eliminate all disputes
- replace human judgment in high-risk cases

This model provides an uncertainty-aware structure for fairer contribution assessment.

---

## Design Philosophy

Contribution is not always a fixed number.

In creative, technical, and AI-mediated environments, contribution often behaves like a flexible structure.

It bends with evidence.  
It shifts with new traces.  
It narrows with stronger proof.  
It widens under uncertainty.  
It may require review when conflict appears.

Therefore, a mature royalty or attribution system should not pretend to have perfect certainty.

It should preserve flexibility without losing accountability.

The system must be like a willow:

> flexible enough to bend with uncertainty,  
> rooted enough to remain auditable.

---

## Current Status

```text
Version: v0.1
Status: Draft
Schema: JSON Schema Draft 2020-12
Validation: GitHub Actions
```

This repository currently provides:

```text
schemas/
  contribution-tolerance-band-v0.1.schema.json

examples/
  contribution-tolerance-band.sample.json

docs/
  contribution-tolerance-band-model.md
  relationship-to-royalty-os.md
  relationship-to-ksd.md
  relationship-to-trace-protocol.md
  relationship-to-dispute-registry.md
  allocation-readiness.md
  review-status-notes.md
  governance-bridge-notes.md

.github/workflows/
  validate-specs.yml
```

---

## License

See [`LICENSE`](LICENSE).

---

## Summary

Contribution Tolerance Band Model v0.1 introduces:

- interval-based contribution estimation
- explainable tolerance bands
- evidence-aware uncertainty
- estimator consensus
- range overlap handling
- review triggers
- allocation readiness
- shared pool handling
- dispute-aware allocation guidance
- governance-aware review flow
- machine-readable validation

Its central principle is:

> Do not force exactness where exactness cannot be justified.  
> Make uncertainty visible, bounded, explainable, and governable.
