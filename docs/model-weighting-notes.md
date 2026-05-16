# Model Weighting Notes

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Band Width Function, Allocation Readiness, Trace Protocol, KSD, Structure Fingerprint, Dispute Registry

---

## One-Line Summary

Model Weighting Notes define how multiple estimators should be weighted when producing contribution estimates, tolerance bands, and allocation recommendations.

Contribution Tolerance Band Model should not depend on a single estimator.

It should combine multiple signals in a controlled, explainable, and auditable way.

---

## Why Model Weighting Matters

Contribution assessment may depend on many kinds of estimators.

Examples:

- structure estimator
- trace estimator
- provenance estimator
- similarity estimator
- human reviewer
- community review layer
- dispute-aware estimator
- domain-specific expert reviewer
- lineage estimator

Each estimator may be useful.

However, no estimator should be treated as perfect.

A structure estimator may overvalue conceptual similarity.  
A provenance estimator may overvalue explicit records.  
A trace estimator may overvalue visible paths.  
A human reviewer may add context, but may also introduce subjective judgment.

Model weighting exists to balance these differences.

---

## Core Principle

Do not let one estimator dominate contribution assessment unless there is a clear reason.

A contribution assessment should be based on a weighted combination of estimator outputs.

```text
weighted_estimate =
  Σ estimator_weight_i * estimator_output_i

The weights should be:

explicit
auditable
configurable
justified by role
adjustable by domain
sensitive to reliability
sensitive to dispute status
Basic Estimator Types

A minimal estimator set may include:

structure_estimator
provenance_estimator
trace_estimator
human_reviewer

A broader estimator set may include:

structure_estimator
provenance_estimator
similarity_estimator
trace_estimator
human_reviewer
community_review
dispute_aware_estimator
hybrid_estimator
domain_expert
other
Structure Estimator

A structure estimator evaluates structural contribution.

It may consider:

KSD records
Structure Fingerprint records
origin question similarity
conceptual architecture
transformation pattern
protocol lineage
semantic skeleton
design grammar

Strength:

detects deeper structural influence

Risk:

may overclaim influence from broad structural similarity

Suggested weight:

0.20 - 0.35
Provenance Estimator

A provenance estimator evaluates visible origin records.

It may consider:

timestamps
repository history
commit logs
publication records
signed records
license records
C2PA-style provenance
Content Credentials-style metadata

Strength:

strong for visible, externalized evidence

Risk:

may ignore hidden or structural influence

Suggested weight:

0.20 - 0.35
Trace Estimator

A trace estimator evaluates connection paths.

It may consider:

access trace
reference trace
influence trace
transformation trace
audit trace
derivative trace
dispute trace

Strength:

connects works, contributors, and later outputs

Risk:

may overvalue noisy or incomplete trace paths

Suggested weight:

0.20 - 0.35
Similarity Estimator

A similarity estimator evaluates resemblance between works.

It may consider:

textual similarity
embedding similarity
semantic similarity
structural similarity
code similarity
media similarity

Strength:

useful for initial detection

Risk:

surface similarity does not always mean contribution

Suggested weight:

0.05 - 0.20

Similarity estimation should usually not dominate the assessment.

Human Reviewer

A human reviewer evaluates context, ambiguity, and governance-sensitive factors.

It may consider:

field knowledge
historical context
independent invention risk
common-structure risk
intent and usage context
dispute sensitivity
fairness concerns

Strength:

adds contextual judgment

Risk:

may introduce subjective bias

Suggested weight:

0.10 - 0.30

Human review should be especially important in high-value or disputed cases.

Community Review

Community review may provide broader feedback.

It may consider:

community recognition
public claims
peer review
contributor reputation
repeated references
shared understanding

Strength:

captures distributed social knowledge

Risk:

may be affected by popularity, coordination, or group bias

Suggested weight:

0.05 - 0.20

Community review should be weighted carefully.

Popularity is not proof of contribution.

Dispute-Aware Estimator

A dispute-aware estimator evaluates risk and instability.

It may consider:

open disputes
counter-evidence
prior dispute history
bad-faith dispute patterns
contested trace paths
contested KSD lineage
contested attestations

Strength:

protects allocation from unstable claims

Risk:

may over-penalize legitimate but contested contributions

Suggested weight:

0.10 - 0.25

This estimator may affect both estimated value and tolerance band width.

Domain Expert

A domain expert estimator or reviewer may be used when the field requires specialized judgment.

Examples:

software licensing
music similarity
academic research
visual media
legal attribution
protocol architecture
dataset lineage

Strength:

adds domain-specific reliability

Risk:

may be expensive, slow, or institutionally biased

Suggested weight:

0.10 - 0.35

Domain expert weighting should be stronger in high-risk or high-value cases.

Minimal Weight Profile

A simple v0.1 profile may use:

{
  "structure_estimator": 0.30,
  "provenance_estimator": 0.25,
  "trace_estimator": 0.25,
  "human_reviewer": 0.20
}

Total:

1.00

This profile balances structural evidence, visible proof, trace paths, and human judgment.

Trace-Heavy Weight Profile

Useful when trace records are strong and reliable.

{
  "trace_estimator": 0.35,
  "provenance_estimator": 0.25,
  "structure_estimator": 0.25,
  "human_reviewer": 0.15
}

Use when:

trace paths are clear
provenance records are reliable
direct evidence is available
dispute risk is low
Structure-Heavy Weight Profile

Useful when structural lineage is central.

{
  "structure_estimator": 0.40,
  "trace_estimator": 0.20,
  "provenance_estimator": 0.20,
  "human_reviewer": 0.20
}

Use when:

contribution is conceptual
direct citation is incomplete
KSD evidence is strong
structure fingerprint is distinctive
protocol or architecture lineage matters

Caution:

Do not use structure-heavy weighting when the structure is generic or common.
Provenance-Heavy Weight Profile

Useful when visible records are the strongest evidence.

{
  "provenance_estimator": 0.40,
  "trace_estimator": 0.25,
  "structure_estimator": 0.20,
  "human_reviewer": 0.15
}

Use when:

publication records are clear
repository history is strong
signed records exist
timestamps are reliable
direct citations are available

Caution:

This profile may underweight hidden structural influence.
Dispute-Sensitive Weight Profile

Useful when the case is contested.

{
  "dispute_aware_estimator": 0.25,
  "human_reviewer": 0.25,
  "trace_estimator": 0.20,
  "structure_estimator": 0.15,
  "provenance_estimator": 0.15
}

Use when:

dispute risk is high
counter-evidence exists
trace path is challenged
KSD lineage is challenged
allocation value is high

This profile should usually trigger review or provisional handling.

Weight Sum Rule

Estimator weights should sum to 1.0.

Example:

{
  "structure_estimator": 0.30,
  "provenance_estimator": 0.25,
  "trace_estimator": 0.25,
  "human_reviewer": 0.20
}

If weights do not sum to 1.0, they should be normalized.

normalized_weight_i = raw_weight_i / Σ raw_weight_i
Weighted Estimated Value

The central estimated value may be calculated as:

weighted_estimated_value =
  Σ weight_i * estimated_value_i

Example:

Structure Estimator:   0.48 × 0.30 = 0.144
Provenance Estimator:  0.45 × 0.25 = 0.1125
Trace Estimator:       0.46 × 0.25 = 0.115
Human Reviewer:        0.44 × 0.20 = 0.088

Result:

weighted_estimated_value = 0.4595

Rounded:

estimated_value = 0.46
Weighted Tolerance Band

Tolerance bands may also be weighted.

weighted_tolerance_band =
  Σ weight_i * tolerance_band_i

Example:

Structure Estimator:   0.04 × 0.30 = 0.012
Provenance Estimator:  0.04 × 0.25 = 0.010
Trace Estimator:       0.05 × 0.25 = 0.0125
Human Reviewer:        0.06 × 0.20 = 0.012

Result:

weighted_tolerance_band = 0.0465

Rounded:

tolerance_band = 0.05

However, this should be combined with the Band Width Function when possible.

Estimator Variance

Estimator variance measures disagreement.

Example:

Estimator outputs:
0.48, 0.45, 0.46, 0.44

Low variance.

Example:

Estimator outputs:
0.20, 0.55, 0.70, 0.35

High variance.

High variance should:

widen tolerance_band
lower estimator_agreement
increase review likelihood
Estimator Agreement

Estimator agreement indicates how strongly estimators converge.

A simple conceptual relation:

estimator_agreement = 1 - normalized_estimator_variance

High agreement means:

narrower band
higher confidence
higher allocation readiness

Low agreement means:

wider band
lower confidence
review_required
Outlier Handling

Some estimator outputs may be outliers.

Example:

Estimator A: 0.46
Estimator B: 0.48
Estimator C: 0.45
Estimator D: 0.90

The system should not automatically accept the outlier.

Possible handling:

flag outlier
reduce outlier weight
require explanation
trigger review if high impact

Outlier handling should be auditable.

Median-Based Aggregation

In some cases, median may be safer than mean.

Example:

0.45, 0.46, 0.48, 0.90

Mean:

0.5725

Median:

0.47

Median reduces the effect of outliers.

Suggested use:

Use median or trimmed mean when estimator outputs contain suspicious extremes.
Trimmed Mean

A trimmed mean removes extreme values before averaging.

Example:

Inputs:
0.20, 0.45, 0.46, 0.48, 0.90

Remove lowest and highest:

0.45, 0.46, 0.48

Trimmed mean:

0.463

This may be useful when estimator manipulation or noise is suspected.

Confidence-Adjusted Weighting

Estimator weights may be adjusted by confidence.

adjusted_weight_i =
  base_weight_i * estimator_confidence_i

Then normalize:

normalized_adjusted_weight_i =
  adjusted_weight_i / Σ adjusted_weight_i

Example:

Structure weight = 0.30, confidence = 0.80
Adjusted = 0.24

Trace weight = 0.25, confidence = 0.60
Adjusted = 0.15

This allows more reliable estimators to contribute more.

Domain-Adjusted Weighting

Different domains may require different weighting.

Text / Essays

Suggested emphasis:

structure_estimator
trace_estimator
human_reviewer
Code

Suggested emphasis:

provenance_estimator
trace_estimator
repository_history
human_reviewer
Research

Suggested emphasis:

citation evidence
provenance_estimator
domain_expert
trace_estimator
Visual Media

Suggested emphasis:

provenance_estimator
similarity_estimator
human_reviewer
C2PA-style provenance
Protocol Architecture

Suggested emphasis:

structure_estimator
KSD
Structure Fingerprint
trace_estimator
human_reviewer

Weights should be domain-aware.

Dispute-Adjusted Weighting

When a case is disputed, weighting should change.

Possible changes:

increase human_reviewer weight
increase dispute_aware_estimator weight
reduce unsupported similarity_estimator weight
reduce weak structural estimator weight
increase provenance_estimator weight if records are strong

This prevents disputed cases from being decided by weak or unstable signals.

Manipulation-Adjusted Weighting

If manipulation risk is detected, the system should adjust weights.

Manipulation may include:

trace spam
artificial citations
fake provenance
circular references
coordinated claims
evidence flooding
retroactive claim insertion

Possible response:

reduce weight of suspicious evidence sources
increase dispute-aware review
increase human review
trigger governance bridge

Uncertainty created by manipulation should not become entitlement.

Weighting and Band Width Function

Model weighting affects the Band Width Function.

High estimator disagreement should increase:

estimator_variance

High estimator agreement should increase:

estimator_agreement

This affects:

tolerance_band
allocation_readiness
review_status

Example:

high estimator variance
→ wider tolerance band
→ review_required
Weighting and Allocation Readiness

Allocation Readiness should use weighting results carefully.

A contribution assessment may be allocation-ready when:

weighted estimate is stable
estimator variance is low
confidence-adjusted weights are strong
no major outliers exist
dispute risk is low
evidence strength is sufficient

If model weighting is unstable, allocation should be delayed or reviewed.

Weighting and Dispute Registry

If a dispute challenges the weighting method, the dispute should be recorded.

Examples:

one estimator was over-weighted
human review was under-weighted
similarity estimator dominated unfairly
provenance evidence was ignored
KSD evidence was treated as final judgment

A disputed weighting profile may require:

review
correction
supersession
recalculation
Weighting and Governance Bridge

Governance Bridge should interpret model weighting as part of decision safety.

It should ask:

Were weights explicit?
Did weights sum to 1.0?
Were weights appropriate for the domain?
Were confidence levels considered?
Were outliers handled?
Was estimator disagreement visible?
Was the weighting profile auditable?

If not, the case may require review.

Suggested JSON Mapping

The current schema supports estimator weights in methodology.estimator_set.

Example:

{
  "methodology": {
    "estimator_set": [
      {
        "estimator_id": "structure-estimator-001",
        "estimator_type": "structure_estimator",
        "weight": 0.30,
        "description": "Evaluates structural similarity and conceptual lineage."
      },
      {
        "estimator_id": "provenance-estimator-001",
        "estimator_type": "provenance_estimator",
        "weight": 0.25,
        "description": "Evaluates timestamps, repository history, and publication records."
      },
      {
        "estimator_id": "trace-estimator-001",
        "estimator_type": "trace_estimator",
        "weight": 0.25,
        "description": "Evaluates trace paths between origin records and later outputs."
      },
      {
        "estimator_id": "human-reviewer-001",
        "estimator_type": "human_reviewer",
        "weight": 0.20,
        "description": "Provides contextual review."
      }
    ]
  }
}
Suggested Future Schema Extension

A future schema version may include explicit weighting metadata.

Example:

{
  "model_weighting": {
    "method": "confidence_adjusted_weighting_v0.1",
    "weight_profile": "minimal_balanced",
    "weights_sum": 1.0,
    "aggregation_method": "weighted_mean",
    "outlier_policy": "flag_and_review",
    "confidence_adjustment": true,
    "domain_adjustment": "protocol_architecture",
    "dispute_adjustment": false
  }
}

This may be added in v0.2 if weighting transparency becomes a formal requirement.

Suggested Future Fields

Possible future fields:

model_weighting.method
model_weighting.weight_profile
model_weighting.weights_sum
model_weighting.aggregation_method
model_weighting.outlier_policy
model_weighting.confidence_adjustment
model_weighting.domain_adjustment
model_weighting.dispute_adjustment
model_weighting.weighting_notes
Anti-Gaming Rule

A contributor should not benefit from manipulating estimator weights.

Examples of abuse:

forcing a similarity estimator to dominate
flooding the system with weak trace evidence
suppressing provenance evidence
over-weighting friendly human reviewers
using coordinated community review
hiding estimator disagreement

Important rule:

Weighting must be transparent enough to be challenged.

If the weighting profile cannot be explained, the assessment should not be allocation-ready.

What Model Weighting Should Not Do

Model Weighting should not:

replace contribution assessment
replace Band Width Function
replace Dispute Registry
determine legal ownership
hide estimator disagreement
overfit to one preferred outcome
allow a single estimator to dominate without justification
turn weak evidence into strong allocation
erase uncertainty

It provides a controlled method for combining estimators.

It does not decide everything by itself.

Design Philosophy

Different estimators see different parts of contribution.

One sees structure.
One sees trace.
One sees provenance.
One sees context.
One sees dispute risk.

No single estimator sees the whole field.

Model Weighting allows these partial views to form a balanced assessment.

The goal is not to crown one estimator.

The goal is to create a stable center of gravity.

Summary

Model Weighting Notes define how multiple estimators should be combined.

The core rule is:

A contribution assessment should not depend on a single estimator unless the weighting profile explicitly justifies it.

Good model weighting makes contribution assessment:

more stable
more explainable
more auditable
more resistant to bias
more resistant to manipulation
more useful for allocation readiness
more compatible with dispute handling

Contribution Tolerance Band Model needs model weighting because contribution is multi-dimensional.

The system should not ask one eye to see the whole landscape.
