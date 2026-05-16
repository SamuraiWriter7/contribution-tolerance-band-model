# Contribution Tolerance Band Model v0.1

## Status

Draft v0.1  
Part of the Kazene Royalty OS / Communication Royalty OS architecture.

## One-Line Definition

Contribution Tolerance Band Model v0.1 defines contribution not as a single exact value, but as an interval-based estimate with an explainable tolerance band determined by evidence, structure, trace confidence, estimator agreement, and dispute risk.

## 日本語定義

Contribution Tolerance Band Model v0.1 は、貢献度を単一の正確な値としてではなく、証拠・構造・トレース確度・推定器間の一致度・異議リスクに応じて変動する「許容帯つき区間」として扱うための最小仕様である。

---

# 1. Purpose

In royalty, attribution, and trace-based value distribution systems, one of the hardest problems is determining:

> Who contributed how much?

Exact contribution measurement is often impossible.

Ideas, structures, prompts, code, texts, designs, and conceptual influences may overlap, transform, mutate, or reappear indirectly.  
Therefore, Contribution Tolerance Band Model does not attempt to calculate a perfect contribution value.

Instead, it provides a practical model for handling contribution under uncertainty.

The goal is not perfect precision.  
The goal is fair, explainable, auditable, and dispute-resistant allocation under imperfect evidence.

---

# 2. Core Principle

Contribution should not be treated as a fixed point.

Instead of:

```text
Contributor A: 47%
Contributor B: 38%
Contributor C: 15%

This model treats contribution as a range:

Contributor A: 42% - 50%
Contributor B: 35% - 43%
Contributor C: 12% - 18%

This range is called the Contribution Tolerance Band.

3. Core Formula
Contribution Range = estimated_value ± tolerance_band

Or:

C = μ ± ε

Where:

C = contribution range
μ = estimated contribution value
ε = tolerance band
μ - ε = lower bound
μ + ε = upper bound

Example:

{
  "contributor_id": "contributor_A",
  "estimated_value": 0.46,
  "tolerance_band": 0.04,
  "range": {
    "lower_bound": 0.42,
    "upper_bound": 0.50
  }
}
4. Why a Band Instead of a Point?

A point estimate suggests false precision.

For example:

A = 47%
B = 38%

This appears precise, but the system may not have enough evidence to justify the difference.

A range makes uncertainty visible.

A = 42% - 50%
B = 35% - 43%

Here, A and B partially overlap.
That means the system should avoid excessive ranking and may treat them as near contributors.

This prevents unnecessary disputes over small numerical differences.

5. Good Uncertainty vs Bad Ambiguity

This model distinguishes between controlled uncertainty and uncontrolled ambiguity.

Good Uncertainty

Good uncertainty is explainable.

It comes from:

incomplete but meaningful evidence
partial structural similarity
moderate trace confidence
estimator disagreement within acceptable limits
indirect influence

Example:

A: 42% - 50%

This is acceptable if the band width is justified.

Bad Ambiguity

Bad ambiguity is too broad to be useful.

Example:

A: 10% - 90%

This means the system does not know enough to allocate safely.

In such cases, the result should not be used for automatic allocation.

It should trigger:

human review
dispute handling
evidence request
shared pool allocation
deferred decision
6. Evidence Factors

The tolerance band is determined by several factors.

6.1 Direct Evidence

Direct evidence includes:

citation
explicit reference
timestamp
signature
repository history
commit log
publication record
license record
C2PA-style provenance
Signed Impact Attestation

Direct evidence generally narrows the tolerance band.

strong direct evidence → smaller ε
weak direct evidence → larger ε
6.2 Structural Evidence

Structural evidence includes:

structure fingerprint
KSD record
origin-question similarity
conceptual lineage
transformation pattern
design pattern inheritance
protocol similarity
architectural resemblance

Structural evidence may detect influence even when direct citation is missing.

However, structural evidence alone should usually produce a wider tolerance band than direct evidence.

6.3 Trace Confidence

Trace confidence measures how clearly a contribution can be connected to later outputs.

Examples:

clear trace path
partial trace path
inferred trace path
missing trace path
disputed trace path

Higher trace confidence narrows the band.

Lower trace confidence widens the band.

6.4 Estimator Agreement

Multiple estimators may evaluate contribution.

Examples:

structure estimator
provenance estimator
similarity estimator
human reviewer
community review layer
dispute-aware estimator

If estimators agree, the tolerance band narrows.

If estimators disagree, the tolerance band widens.

6.5 Dispute Risk

Dispute risk reflects the probability that the contribution estimate may be challenged.

High dispute risk widens the band or triggers review.

Dispute risk may increase when:

contributors have overlapping claims
evidence is weak
trace paths conflict
estimator outputs diverge
prior disputes exist
attribution has economic consequences
7. Tolerance Band Calculation

A minimal calculation model:

ε =
  base_uncertainty
+ structure_ambiguity
+ trace_uncertainty
+ estimator_disagreement
+ dispute_risk
- evidence_strength

A more structured version:

epsilon =
  α * structure_ambiguity
+ β * trace_uncertainty
+ γ * estimator_variance
+ δ * dispute_risk
- λ * evidence_strength

Where:

structure_ambiguity = ambiguity of structural contribution
trace_uncertainty = uncertainty in trace relation
estimator_variance = disagreement among estimators
dispute_risk = likelihood of challenge
evidence_strength = strength of supporting evidence
α β γ δ λ = configurable weights
8. Range Overlap Rules
8.1 Overlapping Ranges

If two contribution ranges overlap significantly, the system should avoid strict ranking.

Example:

A: 42% - 50%
B: 39% - 47%

A and B should be treated as near contributors.

Possible outcomes:

equal allocation within a contributor group
shared pool allocation
joint attribution
human review if high-value distribution is involved
8.2 Clearly Separated Ranges

If ranges do not overlap, differentiated allocation may be allowed.

Example:

A: 50% - 60%
B: 25% - 35%
C: 10% - 15%

Here, A can reasonably be treated as the primary contributor.

8.3 Excessively Wide Ranges

If a range is too wide, automatic allocation should be blocked.

Example:

A: 10% - 80%

This should trigger:

review_required = true

Possible outcomes:

request more evidence
send to Dispute Registry
defer allocation
place value into shared pool
mark as unresolved contribution
9. Contribution Layers

For human readability, contribution should also be expressed as layers.

Instead of exposing only numbers, the model may classify contributors as:

Primary Contribution Layer
Near Contribution Layer
Supporting Contribution Layer
Shared Influence Layer
Unresolved / Disputed Layer

Example:

{
  "primary_contribution_layer": ["contributor_A"],
  "near_contribution_layer": ["contributor_B"],
  "supporting_contribution_layer": ["contributor_C"],
  "shared_influence_layer": ["contributor_D", "contributor_E"],
  "unresolved_layer": []
}

This reduces psychological conflict caused by excessive numerical precision.

10. Yin-Yang Balance Interpretation

This model may be interpreted as a Yin-Yang balance system.

Yang Evidence

Yang represents visible, explicit, externalized evidence.

Examples:

citation
signature
timestamp
code commit
publication history
explicit reference
C2PA-style provenance
Yin Influence

Yin represents hidden, structural, indirect, or long-term influence.

Examples:

conceptual resonance
structural similarity
origin-question influence
implicit inspiration
design lineage
cultural diffusion
long-term transformation

A healthy contribution model should not rely only on Yang evidence.
It should also recognize Yin influence.

However, it should not rely only on Yin influence either.
Unverified influence claims must not automatically generate strong allocation rights.

Therefore, the model seeks a middle balance.

Too much Yang → only explicit records matter
Too much Yin → vague influence claims dominate
Middle Balance → evidence and structure are both considered

This is the “willow model” of allocation:

flexible enough to bend, structured enough not to collapse.

11. Allocation Behavior

Contribution Tolerance Band Model does not directly enforce payment.

It provides allocation guidance.

Possible allocation outcomes:

automatic_allocation
pooled_allocation
equalized_allocation
human_review
dispute_registry
deferred_allocation
common_culture_pool
11.1 Automatic Allocation

Allowed when:

evidence is strong
tolerance bands are narrow
estimator agreement is high
dispute risk is low
11.2 Pooled Allocation

Used when:

contributors have overlapping ranges
contributions are difficult to separate
influence is shared
exact ranking would create unnecessary conflict
11.3 Human Review

Required when:

tolerance band is too wide
evidence is conflicting
estimator agreement is low
high-value distribution is involved
11.4 Common Culture Pool

Used when:

influence is real but not individually attributable
origin is unclear
contribution has become broadly cultural
evidence is too weak for personal allocation
12. Minimal JSON Object
{
  "model": "Contribution Tolerance Band Model",
  "version": "0.1",
  "contribution_assessment_id": "ctb-2026-0001",
  "target_work_id": "work-example-001",
  "contributors": [
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
    },
    {
      "contributor_id": "contributor_B",
      "estimated_value": 0.39,
      "tolerance_band": 0.04,
      "range": {
        "lower_bound": 0.35,
        "upper_bound": 0.43
      },
      "confidence": 0.76,
      "evidence_strength": 0.69,
      "trace_confidence": 0.70,
      "estimator_agreement": 0.73,
      "dispute_risk": 0.18,
      "contribution_layer": "near"
    },
    {
      "contributor_id": "contributor_C",
      "estimated_value": 0.15,
      "tolerance_band": 0.03,
      "range": {
        "lower_bound": 0.12,
        "upper_bound": 0.18
      },
      "confidence": 0.68,
      "evidence_strength": 0.61,
      "trace_confidence": 0.58,
      "estimator_agreement": 0.66,
      "dispute_risk": 0.24,
      "contribution_layer": "supporting"
    }
  ],
  "allocation_recommendation": {
    "type": "pooled_allocation",
    "reason": "Primary and near contributor ranges partially overlap.",
    "review_required": false
  }
}
13. Review Triggers

A contribution assessment should trigger review when:

tolerance_band_width > configured_threshold
estimator_agreement < configured_threshold
dispute_risk > configured_threshold
evidence_strength < configured_threshold
range_overlap_conflict = true
high_value_distribution = true

Example:

{
  "review_required": true,
  "review_reasons": [
    "wide_tolerance_band",
    "low_estimator_agreement",
    "high_dispute_risk"
  ]
}
14. Relationship to Royalty OS

Contribution Tolerance Band Model provides the uncertainty-aware contribution layer for Royalty OS.

Royalty OS may use this model to determine:

who may receive allocation
whether allocation should be automatic
whether allocation should be pooled
whether allocation should be deferred
whether a case should be sent to dispute handling

This model does not replace Royalty OS.
It strengthens Royalty OS by preventing false precision in contribution scoring.

15. Relationship to KSD / Structure Fingerprint

KSD and Structure Fingerprint provide structural evidence.

They help determine:

whether two works share structural lineage
whether a question, pattern, or architecture has been inherited
whether similarity is superficial or structural
whether indirect influence exists

Contribution Tolerance Band Model uses this evidence to adjust the tolerance band.

Strong structural evidence narrows uncertainty.
Weak or ambiguous structural evidence widens uncertainty.

16. Relationship to Trace Protocol

Trace Protocol provides trace paths.

These may include:

access trace
influence trace
audit trace
reference trace
transformation trace

Contribution Tolerance Band Model uses trace confidence to determine whether the contribution range should be narrow or wide.

17. Relationship to Signed Impact Attestation

Signed Impact Attestation provides accountable claims.

If an evaluator or institution claims that a contributor had a certain impact, that claim can be included as evidence.

However, a signed claim does not automatically determine final contribution.

It affects:

evidence strength
dispute risk
estimator confidence
review status
18. Relationship to Dispute Registry

If a contribution estimate is challenged, the case may be sent to Dispute Registry.

Dispute Registry may record:

objection
correction
supersession
revocation
reaffirmation
review outcome

Contribution Tolerance Band Model should not hide disputes.
It should make uncertain or contested contribution visible.

19. Non-Goals

This model does not:

determine legal ownership
replace copyright law
prove absolute originality
guarantee perfect fairness
calculate metaphysical truth of influence
enforce payment by itself
eliminate all disputes

This model provides an uncertainty-aware structure for fairer contribution assessment.

20. Design Philosophy

Contribution is not always a fixed number.

In creative, technical, and AI-mediated environments, contribution often behaves like a flexible structure.

It bends with evidence.
It shifts with new traces.
It narrows with stronger proof.
It widens under uncertainty.
It may require review when conflict appears.

Therefore, a mature royalty system should not pretend to have perfect certainty.

It should preserve flexibility without losing accountability.

The system must be like a willow:

flexible enough to bend with uncertainty,
rooted enough to remain auditable.

21. Summary

Contribution Tolerance Band Model v0.1 introduces:

interval-based contribution estimation
explainable tolerance bands
evidence-aware uncertainty
estimator consensus
range overlap rules
review triggers
shared pool handling
dispute-aware allocation guidance

Its central principle is:

Do not force exactness where exactness cannot be justified.
Make uncertainty visible, bounded, explainable, and governable.
