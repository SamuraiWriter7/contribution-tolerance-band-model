# Relationship to Royalty OS

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS

---

## One-Line Summary

Contribution Tolerance Band Model provides the uncertainty-aware contribution assessment layer for Royalty OS.

It helps Royalty OS avoid false precision when determining who contributed how much under imperfect evidence.

---

## Why Royalty OS Needs This Model

Royalty OS aims to support value distribution based on permission, trace, attribution, and allocation.

However, one of the hardest problems in any royalty or attribution system is:

> Who contributed how much?

In many cases, this cannot be measured as a single exact number.

Contribution may come from:

- an original question
- a structural concept
- a protocol design
- a text
- a dataset
- an implementation
- an edit
- a transformation
- a citation
- an indirect influence
- a long-term trace
- a disputed lineage

If Royalty OS treats contribution as a fixed score too early, it may create false precision.

Example:

```text
Contributor A: 47%
Contributor B: 38%
Contributor C: 15%

This looks precise, but the available evidence may not justify such exactness.

Contribution Tolerance Band Model solves this by treating contribution as a range.

Contributor A: 42% - 50%
Contributor B: 35% - 43%
Contributor C: 12% - 18%

This allows Royalty OS to distribute value without pretending to know more than the evidence supports.

Position in the Royalty OS Stack

Contribution Tolerance Band Model sits between trace evidence and allocation decisions.

Permission Layer
  ↓
Trace Layer
  ↓
Evidence / Structure Layer
  ↓
Contribution Tolerance Band Model
  ↓
Allocation Readiness
  ↓
Royalty Allocation
  ↓
Dispute / Review / Revision

In this stack, Contribution Tolerance Band Model does not replace Royalty OS.

It acts as a bridge between evidence and allocation.

Core Role

The core role of this model is to answer:

Is the contribution evidence strong enough for allocation, and if so, within what range?

It does not ask:

What is the perfect contribution percentage?

Instead, it asks:

What is the explainable contribution range under current evidence?

This difference is essential.

Royalty OS should not require perfect certainty before acting.

But it should also not allocate value based on unsupported claims.

Contribution Tolerance Band Model provides the middle path.

Input to the Model

Royalty OS may pass the following inputs into this model:

contributor identifiers
target work identifiers
trace records
access logs
influence traces
structure fingerprints
KSD records
provenance records
publication records
repository histories
signed attestations
human review notes
dispute records
prior allocation records

These inputs are used to estimate contribution ranges.

Output from the Model

The model outputs contribution assessments such as:

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

Royalty OS can use this output to decide whether allocation should be automatic, pooled, deferred, reviewed, or disputed.

Allocation Guidance

Contribution Tolerance Band Model may recommend one of several allocation behaviors.

automatic_allocation
pooled_allocation
equalized_allocation
human_review
dispute_registry
deferred_allocation
common_culture_pool
no_allocation
Automatic Allocation

Automatic allocation may be appropriate when:

evidence is strong
trace confidence is high
estimator agreement is high
dispute risk is low
tolerance bands are narrow
contributor ranges are clearly separated

Example:

Contributor A: 55% - 60%
Contributor B: 25% - 30%
Contributor C: 10% - 15%

In this case, Royalty OS may safely treat Contributor A as the primary contributor.

Pooled Allocation

Pooled allocation may be appropriate when contribution ranges overlap.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

Here, A and B are close enough that strict ranking may create unnecessary conflict.

Royalty OS may treat them as near contributors and allocate through a shared pool or equalized group.

Example:

Primary / Near Contributor Pool: 80%
Supporting Contributor Pool: 15%
Shared Influence Pool: 5%

This reduces disputes caused by excessive numerical precision.

Equalized Allocation

Equalized allocation may be appropriate when contributors occupy the same contribution layer.

Example:

Contributor A: 40% - 48%
Contributor B: 41% - 49%

In this case, Royalty OS may decide that the difference is not meaningful enough to justify separate treatment.

The contributors may receive equal allocation within the same layer.

Deferred Allocation

Deferred allocation may be appropriate when evidence is incomplete.

Example:

Contributor A: 20% - 70%

This range is too wide for safe automatic allocation.

Royalty OS may defer allocation until additional evidence is available.

Common Culture Pool

Some influence may be real but not individually attributable.

This may happen when:

the origin is unclear
the structure has become widely diffused
the influence is cultural rather than individual
evidence is too weak for personal allocation
multiple unresolved sources overlap

In such cases, Royalty OS may route value into a common culture pool rather than assigning it to a specific individual.

This prevents unsupported claims from becoming automatic rights.

Relationship to Allocation Readiness

Contribution Tolerance Band Model can feed into Allocation Readiness.

Allocation Readiness may ask:

Is this contribution assessment ready for allocation?

Contribution Tolerance Band Model helps answer this by providing:

tolerance band width
confidence score
evidence strength
trace confidence
estimator agreement
dispute risk
review status
allocation recommendation

If the band is narrow and evidence is strong, the case may be allocation-ready.

If the band is wide or contested, the case should not move directly into allocation.

Relationship to Dispute Handling

Royalty OS should not treat disputes as system failures.

Disputes are part of contribution assessment under uncertainty.

Contribution Tolerance Band Model supports dispute handling by making uncertainty explicit.

A case may be sent to Dispute Registry when:

ranges overlap in a conflict-sensitive way
contributor claims conflict
evidence is weak
counter-evidence exists
estimator agreement is low
dispute risk is high
high-value allocation is involved

This allows Royalty OS to route conflict into a governed review process instead of forcing premature allocation.

Relationship to Trace Protocol

Trace Protocol provides the trace paths.

Contribution Tolerance Band Model interprets those trace paths as contribution evidence.

For example:

Trace Protocol:
A influenced B through trace path X.

Contribution Tolerance Band Model:
A's contribution range is estimated at 42% - 50% with moderate-to-high confidence.

Trace Protocol says what is connected.

Contribution Tolerance Band Model estimates how strongly that connection may count toward contribution.

Royalty OS then decides what kind of allocation behavior is appropriate.

Relationship to KSD / Structure Fingerprint

KSD and Structure Fingerprint provide structural evidence.

They help detect cases where contribution exists at the level of:

question structure
conceptual architecture
protocol design
transformation pattern
lineage relation
structural similarity

Contribution Tolerance Band Model uses these signals to adjust contribution ranges.

Strong structure evidence may narrow uncertainty.

Weak or ambiguous structure evidence may widen uncertainty.

This allows Royalty OS to consider not only visible citations, but also deeper structural influence.

Relationship to Signed Impact Attestation

Signed Impact Attestation provides accountable claims about impact.

A signed attestation may say:

Contributor A had significant structural impact on Work B.

Contribution Tolerance Band Model can include that attestation as evidence.

However, an attestation does not automatically determine final allocation.

It may affect:

evidence strength
confidence
dispute risk
review status
estimator agreement

Royalty OS should treat signed attestations as evidence, not as absolute judgment.

Why This Prevents False Precision

Without this model, Royalty OS may be pressured to output exact numbers too early.

That creates risks:

artificial precision
contributor disputes
overconfident allocation
unfair ranking
brittle governance
legal and reputational risk

Contribution Tolerance Band Model prevents this by saying:

If the evidence is uncertain, the score must show uncertainty.

This is the central protection.

The Willow Principle

Royalty OS should not be a rigid scale that breaks under uncertainty.

It should behave more like a willow.

It bends with new evidence.

It shifts when traces change.

It narrows when proof strengthens.

It widens when uncertainty grows.

It sends conflict to review when needed.

This flexibility is not weakness.

It is what allows the system to remain fair, auditable, and durable.

Example Royalty OS Flow
1. A target work is submitted for royalty assessment.

2. Royalty OS collects trace records, structure fingerprints, attestations, and provenance data.

3. Contribution Tolerance Band Model estimates contribution ranges.

4. The model identifies whether ranges are narrow, overlapping, wide, or disputed.

5. Allocation Readiness determines whether the case can move forward.

6. Royalty OS performs one of the following:
   - automatic allocation
   - pooled allocation
   - equalized allocation
   - deferred allocation
   - dispute registry routing
   - common culture pool routing

7. All reasoning, evidence, and review status are logged for auditability.
Minimal Integration Pattern

A minimal Royalty OS integration may follow this pattern:

trace_records
+ structure_fingerprints
+ attestations
+ provenance_records
        ↓
Contribution Tolerance Band assessment
        ↓
allocation_recommendation
        ↓
Royalty OS allocation policy

This keeps the model modular.

Royalty OS can use the output without depending on a single scoring method.

What Royalty OS Should Not Do

Royalty OS should not:

treat all contribution scores as exact values
allocate high-value rewards from weak evidence
ignore overlapping contribution ranges
hide uncertainty from contributors
treat structural influence as automatically proven ownership
treat direct citation as the only valid form of contribution
skip dispute handling in contested cases

Contribution Tolerance Band Model exists to prevent these failure modes.

Governance Benefits

By integrating this model, Royalty OS gains:

uncertainty-aware allocation
lower dispute risk
better auditability
clearer review triggers
more explainable contribution assessments
safer handling of indirect influence
better compatibility with trace and provenance systems
stronger protection against false precision
Non-Goals

This model does not:

replace Royalty OS
determine legal ownership
replace copyright law
enforce payment directly
eliminate all disputes
guarantee perfect fairness
prove metaphysical originality
decide all allocation cases automatically

It provides a structured contribution assessment layer for Royalty OS.

Summary

Contribution Tolerance Band Model strengthens Royalty OS by transforming uncertain contribution claims into explainable ranges.

It allows Royalty OS to distinguish between:

clear allocation
pooled allocation
equalized allocation
deferred allocation
dispute handling
common culture pool routing

Its central role is simple:

Do not force exact contribution values where exactness cannot be justified.

Royalty OS needs this model because value distribution cannot depend on false precision.

A mature royalty system must be flexible enough to bend with uncertainty, and rooted enough to remain auditable.
