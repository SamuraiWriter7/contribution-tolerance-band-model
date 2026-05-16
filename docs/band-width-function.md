# Band Width Function

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Allocation Readiness, Review Status, Governance Bridge, Trace Protocol, KSD, Structure Fingerprint, Dispute Registry

---

## One-Line Summary

Band Width Function defines how the `tolerance_band` width should be determined in Contribution Tolerance Band assessments.

Contribution Tolerance Band Model says:

```text
Contribution Range = estimated_value ± tolerance_band

Band Width Function explains how the tolerance_band should widen or narrow based on evidence, structure, trace confidence, estimator agreement, and dispute risk.

Why This Document Exists

Contribution Tolerance Band Model treats contribution as a range rather than a fixed point.

Example:

Contributor A: 42% - 50%

This range depends on a central value and a band.

estimated_value = 0.46
tolerance_band = 0.04
range = 0.42 - 0.50

The key question is:

How should the tolerance band be calculated?

If the band is too narrow, the system creates false precision.
If the band is too wide, the system becomes vague and unusable.

Band Width Function defines the middle path.

Core Principle

The tolerance band should reflect uncertainty.

strong evidence → narrower band
weak evidence → wider band

clear trace → narrower band
missing trace → wider band

high estimator agreement → narrower band
low estimator agreement → wider band

low dispute risk → narrower band
high dispute risk → wider band

The band should not be arbitrary.

It should be explainable, bounded, and auditable.

Core Formula

A minimal conceptual formula:

epsilon =
  base_uncertainty
+ structure_ambiguity
+ trace_uncertainty
+ estimator_disagreement
+ dispute_risk
- evidence_strength

A more configurable version:

epsilon =
  α * structure_ambiguity
+ β * trace_uncertainty
+ γ * estimator_variance
+ δ * dispute_risk
- λ * evidence_strength
+ κ * base_uncertainty

Where:

epsilon = tolerance band width
structure_ambiguity = uncertainty in structural contribution
trace_uncertainty = uncertainty in trace path
estimator_variance = disagreement among estimators
dispute_risk = likelihood of challenge
evidence_strength = strength of supporting evidence
base_uncertainty = minimum uncertainty floor
α, β, γ, δ, λ, κ = configurable weights
Why Base Uncertainty Is Needed

Even strong assessments should not pretend to be perfectly exact.

A small base uncertainty should remain because:

contribution is contextual
evidence can be incomplete
future evidence may appear
estimator outputs may shift
human interpretation may vary

Example:

base_uncertainty = 0.02

This means even a strong contribution estimate may retain a minimum band.

estimated_value = 0.46
tolerance_band = 0.02
range = 0.44 - 0.48

This prevents false exactness.

Input Factors

Band Width Function may use the following input factors:

evidence_strength
structure_ambiguity
trace_uncertainty
estimator_variance
estimator_agreement
dispute_risk
temporal_uncertainty
counter_evidence_strength
manipulation_risk
value_at_risk

Not every implementation needs every factor.

A minimal v0.1 implementation may use:

evidence_strength
trace_uncertainty
structure_ambiguity
estimator_variance
dispute_risk
Evidence Strength

Evidence strength measures how well the contribution claim is supported.

Strong evidence may include:

direct citation
publication record
timestamp
repository history
commit log
signed attestation
clear trace path
strong KSD record
high-quality provenance
reliable human review

Weak evidence may include:

vague similarity
missing source record
unsupported influence claim
generic structure
weak provenance
low-quality citation
unclear contributor identity

Effect:

higher evidence_strength → narrower tolerance_band
lower evidence_strength  → wider tolerance_band
Structure Ambiguity

Structure ambiguity measures how unclear the structural relationship is.

Low structure ambiguity means:

structure is distinctive
lineage is specific
transformation path is clear
KSD evidence is strong
structure fingerprint is meaningful
independent invention is less likely

High structure ambiguity means:

similarity is generic
structure is common
lineage is vague
multiple origins are plausible
independent invention is possible
KSD evidence is disputed

Effect:

lower structure_ambiguity → narrower tolerance_band
higher structure_ambiguity → wider tolerance_band
Trace Uncertainty

Trace uncertainty measures how unclear or incomplete the trace path is.

Low trace uncertainty means:

clear trace path exists
timestamped records exist
references are explicit
provenance supports the claim
access or transformation path is visible

High trace uncertainty means:

trace path is missing
trace path is inferred
trace records conflict
provenance is weak
trace manipulation is suspected

Effect:

lower trace_uncertainty → narrower tolerance_band
higher trace_uncertainty → wider tolerance_band
Estimator Variance

Estimator variance measures disagreement among estimators.

Estimators may include:

structure estimator
provenance estimator
trace estimator
similarity estimator
human reviewer
community review layer
dispute-aware estimator

Example:

Estimator A: 0.44
Estimator B: 0.46
Estimator C: 0.47

Low variance.

Example:

Estimator A: 0.20
Estimator B: 0.55
Estimator C: 0.70

High variance.

Effect:

lower estimator_variance → narrower tolerance_band
higher estimator_variance → wider tolerance_band
Estimator Agreement

Estimator agreement is the inverse of estimator variance.

High agreement means multiple estimators converge.

Low agreement means estimators disagree.

Effect:

higher estimator_agreement → narrower tolerance_band
lower estimator_agreement  → wider tolerance_band

Implementation note:

estimator_variance and estimator_agreement should not both be double-counted unless the methodology explicitly defines how they interact.

For v0.1, using one of them is sufficient.

Dispute Risk

Dispute risk measures the likelihood that the contribution assessment may be challenged.

Dispute risk may increase when:

ranges overlap
contributors have competing claims
evidence is weak
trace paths conflict
KSD lineage is disputed
signed attestation is challenged
allocation has high economic value
prior disputes exist
counter-evidence exists

Effect:

lower dispute_risk → narrower tolerance_band
higher dispute_risk → wider tolerance_band

If dispute risk exceeds a configured threshold, the case may trigger review.

Counter-Evidence Strength

Counter-evidence may challenge the contribution claim.

Examples:

alternative origin claim
independent invention claim
conflicting timestamp
disputed trace path
invalidated attestation
manipulated provenance
common-structure claim

Effect:

strong counter_evidence → wider tolerance_band
strong counter_evidence → higher review likelihood

Counter-evidence should not be ignored.

It should either widen the band, trigger review, or route the case to Dispute Registry.

Temporal Uncertainty

Temporal uncertainty measures how contribution confidence changes over time.

Uncertainty may increase when:

records become stale
trace paths become harder to verify
many derivative layers appear
influence becomes culturally diffused
provenance becomes incomplete

Uncertainty may decrease when:

new evidence appears
lineage is clarified
disputes are resolved
records are verified
additional attestations are added

Effect:

higher temporal_uncertainty → wider tolerance_band
lower temporal_uncertainty  → narrower tolerance_band

Temporal behavior may be defined in a separate document.

Manipulation Risk

Manipulation risk measures whether the evidence environment may have been gamed.

Possible manipulation includes:

trace spam
artificial self-citation
fake provenance
circular references
retroactive attribution attempts
coordinated claims
low-quality evidence flooding
artificial range inflation

Effect:

higher manipulation_risk → wider tolerance_band
higher manipulation_risk → review_required

The system should not reward uncertainty created by manipulation.

Value at Risk

Value at risk reflects the economic or institutional significance of the allocation.

High-value cases should require stricter governance.

Effect:

higher value_at_risk → stricter thresholds
higher value_at_risk → review more likely

Value at risk should not necessarily widen the mathematical band.

However, it may lower the threshold for review.

Minimal v0.1 Band Width Model

A minimal v0.1 model may use:

epsilon =
  0.02
+ 0.20 * structure_ambiguity
+ 0.20 * trace_uncertainty
+ 0.20 * estimator_variance
+ 0.20 * dispute_risk
- 0.20 * evidence_strength

Then clamp the result:

epsilon = min(max(epsilon, min_band), max_band)

Example policy:

min_band = 0.02
max_band = 0.30

This prevents the band from becoming unrealistically narrow or unusably wide.

Clamping

Clamping keeps the tolerance band within safe limits.

epsilon = min(max(raw_epsilon, min_band), max_band)

Where:

raw_epsilon = calculated band before limits
min_band = minimum allowed band
max_band = maximum allowed band

Example:

raw_epsilon = 0.005
min_band = 0.02
epsilon = 0.02

Example:

raw_epsilon = 0.42
max_band = 0.30
epsilon = 0.30

Clamping prevents false exactness and runaway ambiguity.

Band Width Classes

The band width may be classified into practical levels.

0.00 - 0.05  → narrow
0.05 - 0.10  → moderate
0.10 - 0.15  → wide
0.15 - 0.30  → very wide
0.30+        → unstable

Suggested interpretation:

Band Width	Meaning	Suggested Handling
narrow	High stability	Allocation may proceed if other signals are strong
moderate	Acceptable uncertainty	Allocation or pooling may proceed
wide	Caution required	Review recommended
very wide	Unstable	Review required or deferred
unstable	Not reliable	Do not allocate automatically

Thresholds should be configurable by domain.

Example Calculation: Strong Evidence

Input:

base_uncertainty = 0.02
structure_ambiguity = 0.10
trace_uncertainty = 0.12
estimator_variance = 0.08
dispute_risk = 0.10
evidence_strength = 0.85

Formula:

epsilon =
  0.02
+ 0.20 * 0.10
+ 0.20 * 0.12
+ 0.20 * 0.08
+ 0.20 * 0.10
- 0.20 * 0.85

Result:

epsilon = -0.07
clamped to min_band = 0.02

Output:

estimated_value = 0.46
tolerance_band = 0.02
range = 0.44 - 0.48

Interpretation:

Strong evidence creates a narrow band.
Example Calculation: Moderate Evidence

Input:

base_uncertainty = 0.02
structure_ambiguity = 0.25
trace_uncertainty = 0.30
estimator_variance = 0.18
dispute_risk = 0.22
evidence_strength = 0.60

Formula:

epsilon =
  0.02
+ 0.20 * 0.25
+ 0.20 * 0.30
+ 0.20 * 0.18
+ 0.20 * 0.22
- 0.20 * 0.60

Result:

epsilon = 0.09

Output:

estimated_value = 0.46
tolerance_band = 0.09
range = 0.37 - 0.55

Interpretation:

Moderate uncertainty produces a moderate-to-wide band.
Review may be recommended depending on allocation value.
Example Calculation: Weak Evidence

Input:

base_uncertainty = 0.02
structure_ambiguity = 0.60
trace_uncertainty = 0.70
estimator_variance = 0.50
dispute_risk = 0.65
evidence_strength = 0.25

Formula:

epsilon =
  0.02
+ 0.20 * 0.60
+ 0.20 * 0.70
+ 0.20 * 0.50
+ 0.20 * 0.65
- 0.20 * 0.25

Result:

epsilon = 0.46
clamped to max_band = 0.30

Output:

estimated_value = 0.46
tolerance_band = 0.30
range = 0.16 - 0.76

Interpretation:

The band is too wide for automatic allocation.
Review or deferral is required.
Range Calculation

Once epsilon is calculated, the range is:

lower_bound = estimated_value - epsilon
upper_bound = estimated_value + epsilon

Bounds should be clamped between 0.0 and 1.0.

lower_bound = max(0.0, estimated_value - epsilon)
upper_bound = min(1.0, estimated_value + epsilon)

Example:

estimated_value = 0.04
epsilon = 0.10

lower_bound = 0.00
upper_bound = 0.14
Review Trigger Thresholds

A band width may trigger review.

Suggested thresholds:

epsilon > 0.10 → review recommended
epsilon > 0.15 → review required
epsilon > 0.30 → not ready or deferred

Additional review triggers:

evidence_strength < 0.50
trace_confidence < 0.50
estimator_agreement < 0.60
dispute_risk > 0.35
counter_evidence_present = true
high_value_distribution = true

These thresholds should be configurable.

Anti-Gaming Rule

A wider band should not create a stronger claim.

Important principle:

Wider uncertainty should not mean wider entitlement.

If a contributor has a very wide band, that should indicate uncertainty, not automatic priority.

Example:

Contributor A: 10% - 90%

This does not mean Contributor A should receive a large share.

It means the system lacks enough certainty.

Recommended handling:

review_required
deferred_allocation
common_culture_pool
disputed_pool
Anti-Gaming: Artificial Ambiguity

A bad actor may try to create uncertainty deliberately.

Examples:

vague contribution claims
trace spam
weak self-references
fake provenance
broad structure claims
artificial overlap with many works

Band Width Function should avoid rewarding this behavior.

If uncertainty appears artificial, the model should:

increase manipulation_risk
increase dispute_risk
trigger review
block automatic allocation
Relationship to Allocation Readiness

Band Width Function directly affects Allocation Readiness.

Example:

narrow band + strong evidence → allocation_ready
moderate band + overlap → pooled_ready
wide band + weak evidence → review_required
very wide band → deferred or not_ready

Allocation Readiness should not rely only on estimated_value.

It should rely on:

estimated_value
tolerance_band
evidence_strength
trace_confidence
estimator_agreement
dispute_risk
review_status
Relationship to Review Status

Band width may determine review status.

Example:

epsilon <= 0.10 → active if other signals are stable
epsilon > 0.10 → review_required may be recommended
epsilon > 0.15 → review_required
epsilon > 0.30 → not_ready or deferred

Review status should reflect whether the band is stable enough to use.

Relationship to Dispute Registry

High dispute risk or counter-evidence may widen the band.

If the band widens because of a formal challenge, the case may be routed to Dispute Registry.

Example:

dispute_risk = 0.75
counter_evidence_present = true
epsilon increases
assessment_status = disputed

Dispute Registry then records the challenge and outcome.

Relationship to Trace Protocol

Trace Protocol affects band width through:

trace_confidence
trace_uncertainty
trace_quality
trace_density
trace_dispute_status
trace_manipulation_risk

Clear trace paths narrow the band.

Missing, inferred, or disputed trace paths widen the band.

Relationship to KSD / Structure Fingerprint

KSD affects band width through:

structure_ambiguity
structural_evidence_strength
lineage_clarity
common_structure_risk
independent_invention_risk

Strong and specific KSD evidence narrows the band.

Generic or disputed structure evidence widens the band.

Relationship to Signed Impact Attestation

Signed Impact Attestation may affect band width through:

evidence_strength
estimator_agreement
dispute_risk
counter_evidence_strength

A strong, clear, uncontested attestation may narrow the band.

A disputed or vague attestation may widen the band or trigger review.

Relationship to Governance Bridge

Governance Bridge should interpret band width as a governance signal.

Example:

narrow band → governance may allow allocation
wide band → governance may require review
disputed band → governance routes to Dispute Registry
unstable band → governance blocks allocation

Band Width Function provides the numerical signal.

Governance Bridge decides what the system should do with that signal.

Suggested Future Schema Extension

A future schema version may include explicit band calculation metadata.

Example:

{
  "band_width_function": {
    "method": "weighted_uncertainty_v0.1",
    "base_uncertainty": 0.02,
    "min_band": 0.02,
    "max_band": 0.30,
    "weights": {
      "structure_ambiguity": 0.20,
      "trace_uncertainty": 0.20,
      "estimator_variance": 0.20,
      "dispute_risk": 0.20,
      "evidence_strength": -0.20
    },
    "raw_epsilon": 0.09,
    "final_epsilon": 0.09,
    "band_class": "moderate"
  }
}

For v0.1, this can be documented without requiring schema changes.

Suggested Future Fields

Possible future fields:

band_width_function.method
band_width_function.base_uncertainty
band_width_function.min_band
band_width_function.max_band
band_width_function.raw_epsilon
band_width_function.final_epsilon
band_width_function.band_class
band_width_function.weights
band_width_function.calculation_notes

These fields may be added in v0.2 if calculation transparency becomes part of the formal schema.

What Band Width Function Should Not Do

Band Width Function should not:

determine legal ownership
decide final allocation by itself
replace human review
replace Dispute Registry
treat uncertainty as entitlement
hide estimator disagreement
collapse disputed evidence into false precision
claim mathematical certainty where none exists

It calculates or explains band width.

It does not govern the entire system.

Design Philosophy

A contribution band should behave like a willow.

It should bend when evidence is uncertain.

It should narrow when evidence is strong.

It should widen when traces are unclear.

It should pause when disputes arise.

It should not break under uncertainty.

The goal is not perfect precision.

The goal is controlled flexibility.

Summary

Band Width Function defines how the tolerance band should be determined.

It turns uncertainty into a visible, bounded, and explainable range.

Its central rule is:

The stronger the evidence, the narrower the band.
The weaker or more disputed the evidence, the wider the band.

This function is essential because Contribution Tolerance Band Model depends not only on the estimated contribution value, but on how much uncertainty surrounds that value.

Without a band width function, the model has a range but no controlled way to determine its width.

With it, the model becomes a governed system for handling contribution under uncertainty.
