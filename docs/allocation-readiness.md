# Allocation Readiness

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Royalty OS, Trace Protocol, KSD, Structure Fingerprint, Dispute Registry, Signed Impact Attestation

---

## One-Line Summary

Allocation Readiness defines when a Contribution Tolerance Band assessment is sufficiently stable to be used for allocation.

Contribution Tolerance Band Model estimates contribution under uncertainty.  
Allocation Readiness decides whether that estimate is ready to affect value distribution.

---

## Why Allocation Readiness Matters

Contribution assessment does not automatically mean allocation should proceed.

A contribution range may exist, but it may still be:

- too wide
- weakly supported
- disputed
- based on incomplete trace evidence
- based on low estimator agreement
- sensitive to counter-evidence
- too high-value to allocate automatically
- dependent on unresolved review

Therefore, Royalty OS should not move directly from contribution estimate to allocation.

It needs a readiness gate.

Allocation Readiness provides that gate.

---

## Basic Relationship

```text
Contribution Tolerance Band Assessment
        ↓
Allocation Readiness Check
        ↓
Ready / Not Ready / Review Required
        ↓
Royalty OS Allocation Policy

Contribution Tolerance Band Model answers:

What is the contribution range?

Allocation Readiness answers:

Is this contribution range stable enough to use for allocation?

Core Principle

Do not allocate from unstable uncertainty.

A contribution assessment should be allocation-ready only when uncertainty is bounded, evidence is sufficient, and dispute risk is acceptable.

The purpose is not to block allocation forever.

The purpose is to prevent premature allocation from weak or contested assessments.

Readiness States

An assessment may have one of several readiness states.

allocation_ready
review_required
deferred
disputed
pooled_ready
common_culture_pool_ready
not_ready
allocation_ready

Use when:

tolerance bands are narrow
evidence strength is high
trace confidence is high
estimator agreement is high
dispute risk is low
no major counter-evidence exists
ranges are clearly separated or safely handled

Example:

Contributor A: 55% - 60%
Contributor B: 25% - 30%
Contributor C: 10% - 15%

This may proceed to automatic allocation.

review_required

Use when the assessment may be usable, but requires additional review.

Triggers include:

wide tolerance bands
overlapping ranges
low estimator agreement
moderate dispute risk
conflicting evidence
high-value allocation
manual review request

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

This may not be wrong, but strict allocation should not proceed without review or pooling.

deferred

Use when allocation should be postponed.

Triggers include:

missing trace records
incomplete evidence
uncertain contributor identity
unresolved provenance
unavailable review
pending dispute

Example:

Contributor A: 20% - 70%

This range is too wide for reliable allocation.

disputed

Use when an assessment has been formally challenged.

Triggers include:

open dispute record
counter-evidence
challenged trace path
challenged KSD lineage
disputed attestation
contributor inclusion or exclusion challenge

Disputed assessments should generally not proceed to automatic allocation.

They may move to:

disputed_pool
deferred_allocation
human_review
Dispute Registry
pooled_ready

Use when individual precision is not justified, but group allocation is reasonable.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%
Contributor C: 12% - 18%

A and B may be treated as a near-contributor pool.

Possible allocation:

Primary / Near Contributor Pool: 80%
Supporting Contributor Pool: 15%
Shared Influence Pool: 5%

This state is useful when strict ranking would create false precision.

common_culture_pool_ready

Use when influence is real but not individually attributable.

This may apply when:

origin is unclear
structure is broadly shared
multiple plausible sources exist
independent invention is plausible
evidence is too weak for individual allocation
cultural diffusion is stronger than individual lineage

Example:

Influence detected, but no specific contributor can be assigned with sufficient confidence.

Allocation may be routed to a common culture pool.

not_ready

Use when the assessment is not stable enough for any allocation decision.

Triggers include:

extremely wide tolerance bands
very low evidence strength
very low trace confidence
high manipulation risk
missing required records
unresolved identity issues
severe estimator disagreement

Example:

Contributor A: 5% - 90%

This should not drive allocation.

Readiness Inputs

Allocation Readiness may use the following inputs:

tolerance_band_width
evidence_strength
trace_confidence
estimator_agreement
estimator_variance
dispute_risk
range_overlap_status
counter_evidence_status
assessment_status
review_required
review_reasons
allocation_recommendation
value_at_risk
Minimal Readiness Formula

A simple readiness model may be expressed as:

allocation_readiness =
  evidence_strength
+ trace_confidence
+ estimator_agreement
- tolerance_band_width
- dispute_risk
- estimator_variance

This is not a mandatory formula.

It is a minimal conceptual model.

The actual implementation may use policy thresholds rather than a single score.

Threshold-Based Readiness

A practical implementation may use threshold rules.

Example:

if tolerance_band <= 0.10
and evidence_strength >= 0.70
and trace_confidence >= 0.70
and estimator_agreement >= 0.75
and dispute_risk <= 0.20
then allocation_ready

Another example:

if tolerance_band > 0.15
or estimator_agreement < 0.60
or dispute_risk > 0.35
then review_required

Another example:

if dispute_risk > 0.70
or counter_evidence_present = true
then disputed
Readiness and Tolerance Band Width

Tolerance band width is one of the most important readiness signals.

A narrow tolerance band indicates that the contribution estimate is relatively stable.

A wide tolerance band indicates that the system should be cautious.

Example:

Narrow:
Contributor A: 42% - 50%

Wide:
Contributor A: 20% - 70%

Wide does not always mean false.

It means allocation should not be automatic.

Suggested Band Width Policy

A minimal policy may look like this:

0.00 - 0.05  → highly stable
0.05 - 0.10  → allocation-ready if other signals are strong
0.10 - 0.15  → review recommended
0.15 - 0.30  → review required
0.30+        → not ready or deferred

These thresholds should be configurable.

Different domains may require different thresholds.

Readiness and Evidence Strength

Evidence strength reflects how well the contribution claim is supported.

Strong evidence may include:

direct citation
publication record
timestamp
repository history
signed attestation
clear trace path
strong KSD record
high-quality provenance

Weak evidence may include:

vague similarity
unsupported influence claim
missing trace path
low-quality citation
generic structural resemblance

Low evidence strength should reduce allocation readiness.

Readiness and Trace Confidence

Trace confidence reflects how clearly a contribution can be connected to a later output.

High trace confidence may support allocation.

Low trace confidence should trigger caution.

Example:

clear trace path → higher readiness
missing trace path → lower readiness
disputed trace path → disputed or review_required
Readiness and Estimator Agreement

Multiple estimators may evaluate the same contribution.

Examples:

structure estimator
provenance estimator
trace estimator
similarity estimator
human reviewer
dispute-aware estimator

If estimators agree, readiness increases.

If estimators disagree, readiness decreases.

Estimator disagreement should not be hidden.

It should widen the tolerance band or trigger review.

Readiness and Range Overlap

Range overlap is not automatically a problem.

It becomes a problem when strict ranking is required.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

This may be handled through pooled allocation.

If pooled allocation is acceptable, the case may be pooled_ready.

If strict individual allocation is required, the case may be review_required.

Readiness and Dispute Risk

Dispute risk reflects the likelihood that the assessment may be challenged.

High dispute risk should lower readiness.

Dispute risk may increase when:

contributors have overlapping claims
evidence is weak
trace records conflict
KSD lineage is challenged
counter-evidence exists
prior disputes exist
allocation has high economic value
Readiness and Value at Risk

High-value allocations should require stricter readiness.

A low-value allocation may tolerate lighter review.

A high-value allocation should require:

stronger evidence
narrower bands
clearer trace paths
lower dispute risk
stronger auditability
possible human review

Example:

high_value_distribution = true
review_required = true

This reduces the risk of costly misallocation.

Readiness and Review Required

The field review_required should block automatic allocation unless the policy explicitly allows provisional handling.

Example:

{
  "review_required": true,
  "review_reasons": [
    "wide_tolerance_band",
    "low_estimator_agreement"
  ]
}

Possible outcomes:

human_review
deferred_allocation
pooled_allocation
dispute_registry
common_culture_pool
Readiness and Dispute Registry

Open disputes should normally reduce allocation readiness.

A case may be routed to Dispute Registry when:

dispute_risk exceeds threshold
counter-evidence exists
manual review is requested
trace path is challenged
KSD lineage is challenged
allocation recommendation is challenged

The assessment may become allocation-ready after:

dispute resolved
assessment reaffirmed
assessment corrected
new assessment supersedes old assessment
pooled allocation accepted
common culture pool routing accepted
Readiness and Pooled Allocation

Pooled allocation is important because not all uncertainty should block distribution.

If contributors occupy overlapping but credible ranges, a pool may be more stable than strict ranking.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

Instead of forcing:

A = 47%
B = 38%

The system may choose:

A/B Near Contributor Pool = 80%

This converts unstable precision into stable group allocation.

Readiness and Common Culture Pool

Some cases should not be forced into individual allocation.

A common culture pool may be appropriate when:

the origin cannot be determined
the structure is common
influence is diffuse
multiple origins are plausible
the evidence is too weak for personal allocation
the contribution has become broadly cultural

This avoids unsupported individual claims while preserving value circulation.

Readiness and Provisional Allocation

Some systems may allow provisional allocation.

Example:

80% released
20% held in disputed pool

Provisional allocation may be useful when:

most of the assessment is stable
only part of the allocation is disputed
delaying all allocation would be unfair
the system can correct later allocations
audit trails are preserved

Provisional allocation should be clearly marked.

It should not be treated as final.

Suggested JSON Extension

A future schema version may include an explicit allocation_readiness object.

Example:

{
  "allocation_readiness": {
    "state": "pooled_ready",
    "readiness_score": 0.76,
    "readiness_reasons": [
      "moderate_tolerance_band",
      "sufficient_evidence_strength",
      "partial_range_overlap"
    ],
    "blocking_issues": [],
    "recommended_next_step": "pooled_allocation"
  }
}

For v0.1, readiness can be inferred from:

allocation_recommendation.type
allocation_recommendation.review_required
review_reasons
contributor tolerance bands
evidence strength
trace confidence
estimator agreement
dispute risk
Suggested Readiness States JSON

Possible future enum:

{
  "state": "allocation_ready"
}

Allowed values:

allocation_ready
review_required
deferred
disputed
pooled_ready
common_culture_pool_ready
not_ready
Example: Allocation Ready
{
  "allocation_readiness": {
    "state": "allocation_ready",
    "readiness_score": 0.88,
    "readiness_reasons": [
      "narrow_tolerance_band",
      "high_evidence_strength",
      "high_trace_confidence",
      "low_dispute_risk"
    ],
    "blocking_issues": [],
    "recommended_next_step": "automatic_allocation"
  }
}
Example: Review Required
{
  "allocation_readiness": {
    "state": "review_required",
    "readiness_score": 0.54,
    "readiness_reasons": [
      "wide_tolerance_band",
      "low_estimator_agreement",
      "range_overlap_conflict"
    ],
    "blocking_issues": [
      "manual_review_required"
    ],
    "recommended_next_step": "human_review"
  }
}
Example: Pooled Ready
{
  "allocation_readiness": {
    "state": "pooled_ready",
    "readiness_score": 0.74,
    "readiness_reasons": [
      "credible_overlapping_ranges",
      "sufficient_evidence_strength",
      "low_dispute_risk"
    ],
    "blocking_issues": [],
    "recommended_next_step": "pooled_allocation"
  }
}
Example: Disputed
{
  "allocation_readiness": {
    "state": "disputed",
    "readiness_score": 0.31,
    "readiness_reasons": [
      "open_dispute",
      "counter_evidence_present",
      "high_dispute_risk"
    ],
    "blocking_issues": [
      "dispute_registry_resolution_required"
    ],
    "recommended_next_step": "dispute_registry"
  }
}
Minimal Decision Table
Condition	Recommended State	Recommended Next Step
Narrow band + strong evidence + low dispute risk	allocation_ready	automatic_allocation
Overlapping but credible ranges	pooled_ready	pooled_allocation
Wide band + incomplete evidence	review_required	human_review
Open dispute + counter-evidence	disputed	dispute_registry
Weak evidence + unclear origin	common_culture_pool_ready	common_culture_pool
Extremely wide band + low confidence	not_ready	deferred_allocation
Anti-Abuse Role

Allocation Readiness helps prevent abuse.

Potential abuse includes:

intentionally vague contribution claims
artificial range inflation
trace spam
fake provenance
weak but repeated claims
strategic disputes
evidence flooding
retroactive attribution attempts

A readiness gate can block premature allocation in these cases.

Important principle:

Wider uncertainty should not automatically produce wider entitlement.

If uncertainty is too wide, allocation should be reviewed, deferred, pooled, or routed to a common culture pool.

What Allocation Readiness Should Not Do

Allocation Readiness should not:

calculate contribution ranges by itself
replace Contribution Tolerance Band Model
replace Royalty OS
replace Dispute Registry
determine legal ownership
enforce payment
guarantee perfect fairness
remove the need for human review in high-risk cases

It is a gate, not the entire system.

Relationship to Royalty OS

Royalty OS uses Allocation Readiness to decide whether allocation can proceed.

Possible paths:

allocation_ready → automatic allocation
pooled_ready → pooled allocation
review_required → human review
disputed → Dispute Registry
deferred → wait for more evidence
common_culture_pool_ready → common culture pool
not_ready → no allocation or deferred allocation

This prevents Royalty OS from acting on unstable contribution assessments.

Relationship to Contribution Tolerance Band Model

Contribution Tolerance Band Model provides:

estimated values
tolerance bands
ranges
confidence scores
evidence strength
trace confidence
estimator agreement
dispute risk
allocation recommendation

Allocation Readiness interprets whether those outputs are stable enough to affect distribution.

The two layers should remain separate.

Tolerance Band Model = assessment
Allocation Readiness = gate
Royalty OS = allocation policy
Relationship to Trace Protocol

Trace Protocol affects readiness through:

trace confidence
trace uncertainty
trace quality
trace density
trace dispute status
trace manipulation risk

Strong trace support increases readiness.

Weak or disputed trace support lowers readiness.

Relationship to KSD / Structure Fingerprint

KSD affects readiness through:

structure ambiguity
structural evidence strength
structural lineage clarity
common-structure risk
independent invention risk

Strong KSD evidence may increase readiness.

Ambiguous or disputed KSD evidence may reduce readiness.

Relationship to Dispute Registry

Dispute Registry affects readiness through:

open dispute status
counter-evidence
review outcome
supersession status
revocation status
reaffirmation status

An unresolved dispute usually blocks automatic allocation.

A resolved dispute may restore readiness.

Relationship to Signed Impact Attestation

Signed Impact Attestation may increase readiness when:

the attestation is clear
the evaluator is accountable
evidence scope is defined
no counter-evidence exists
the attestation aligns with other records

It may reduce readiness when:

the attestation is disputed
evaluator bias is alleged
the scope is unclear
it conflicts with trace or KSD evidence
Example End-to-End Flow
1. A target work is submitted for contribution assessment.

2. Contribution Tolerance Band Model estimates:
   Contributor A: 42% - 50%
   Contributor B: 39% - 47%
   Contributor C: 12% - 18%

3. Allocation Readiness checks:
   - Are the bands narrow enough?
   - Is the evidence strong enough?
   - Are traces clear enough?
   - Do ranges overlap?
   - Is dispute risk acceptable?

4. The system determines:
   state = pooled_ready

5. Royalty OS proceeds with:
   pooled_allocation

6. Audit logs preserve:
   - evidence
   - ranges
   - readiness state
   - allocation recommendation
   - review status
Design Philosophy

Allocation should not be triggered by a number alone.

It should be triggered by a stable relationship between:

range
evidence
trace
agreement
risk
review
governance

This prevents false precision from becoming false distribution.

The system should behave like a gate in a river.

It does not stop the flow of value.

It regulates the flow so that unstable water does not flood the system.

Non-Goals

This document does not define the full Royalty OS allocation policy.

It does not define legal ownership.

It does not enforce payment.

It does not replace Dispute Registry.

It does not determine contribution ranges by itself.

It only defines how to decide whether a contribution assessment is ready to influence allocation.

Summary

Allocation Readiness is the gate between contribution assessment and value distribution.

Contribution Tolerance Band Model makes uncertainty visible.

Allocation Readiness decides whether that uncertainty is stable enough for allocation.

Its core rule is:

Do not allocate from unstable uncertainty.

A mature royalty system should not require perfect certainty.

But it should require enough stability to act responsibly.
