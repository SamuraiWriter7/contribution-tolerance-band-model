# Relationship to Dispute Registry

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Dispute Registry, Trace Protocol, KSD, Structure Fingerprint, Signed Impact Attestation, Royalty OS

---

## One-Line Summary

Dispute Registry provides the governance layer for challenged, uncertain, or contested Contribution Tolerance Band assessments.

Contribution Tolerance Band Model makes uncertainty visible.  
Dispute Registry records what happens when that uncertainty becomes contested.

---

## Why This Relationship Matters

Contribution assessment under uncertainty will sometimes produce disagreement.

A contributor may challenge:

- the estimated contribution value
- the tolerance band width
- the evidence used
- the trace interpretation
- the structural lineage claim
- the allocation recommendation
- the contribution layer
- the review status
- the inclusion or exclusion of a contributor

Contribution Tolerance Band Model should not hide these disputes.

Instead, disputed cases should be routed to Dispute Registry.

This allows the system to preserve trust, auditability, and revision history.

---

## Basic Relationship

```text
Contribution Tolerance Band Model
        ↓
Uncertainty / Overlap / Conflict
        ↓
Dispute Registry
        ↓
Review / Correction / Supersession / Reaffirmation
        ↓
Updated Contribution Assessment

Contribution Tolerance Band Model detects uncertainty and contested contribution ranges.

Dispute Registry records, tracks, and governs the dispute process.

What Dispute Registry Provides

Dispute Registry may record:

objection
correction request
counter-evidence
supersession
revocation
reaffirmation
review outcome
appeal status
final or provisional resolution
updated assessment references

It provides the “afterlife” of a contribution claim.

A contribution assessment should not disappear when challenged.

It should become part of a transparent dispute trail.

Why Tolerance Bands Need Dispute Handling

Tolerance bands reduce false precision, but they do not eliminate conflict.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

A and B overlap.

This may be handled through pooled allocation.

But if Contributor B claims that A’s range is too high, or that B should be classified as primary rather than near, the case may become disputed.

Contribution Tolerance Band Model can indicate:

{
  "review_required": true,
  "review_reasons": [
    "range_overlap_conflict",
    "manual_review_requested"
  ]
}

Dispute Registry then records the challenge and its outcome.

Dispute Is Not System Failure

Dispute should not be treated as failure.

In uncertain contribution systems, dispute is a normal governance event.

A mature royalty or attribution system should expect:

overlapping claims
incomplete evidence
contested trace paths
structural similarity disputes
independent invention claims
disagreement between estimators
changing evidence over time

Dispute Registry turns conflict into structured review.

When to Route to Dispute Registry

A Contribution Tolerance Band assessment may be routed to Dispute Registry when:

tolerance_band is too wide
ranges overlap in a conflict-sensitive way
dispute_risk exceeds threshold
counter-evidence exists
manual review is requested
trace path is challenged
KSD lineage is challenged
Signed Impact Attestation is disputed
allocation recommendation is challenged
high-value distribution is involved
Review Triggers

The following review reasons may indicate possible Dispute Registry routing:

wide_tolerance_band
low_evidence_strength
low_trace_confidence
low_estimator_agreement
high_estimator_variance
high_dispute_risk
range_overlap_conflict
high_value_distribution
counter_evidence_present
manual_review_requested
other

Not all review triggers require a formal dispute.

However, repeated, high-risk, or contested triggers should be recorded.

Dispute Registry as a Governance Layer

Contribution Tolerance Band Model answers:

What is the contribution range under current evidence?

Dispute Registry answers:

What happens when that range is challenged?

This separation is important.

Contribution Tolerance Band Model should not become a court.

Dispute Registry should not become an estimator.

Each layer has its own role.

Tolerance Band Model = uncertainty-aware assessment
Dispute Registry      = contested-claim governance
Royalty OS            = allocation policy
Example: Range Overlap Dispute

Initial assessment:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

The system recommends:

pooled_allocation

Contributor B objects:

B claims that A's range is inflated and B should be classified as co-primary.

Dispute Registry records:

dispute_type: range_overlap_conflict
challenged_record: ctb-2026-0001
claimant: contributor_B
status: open

Possible outcome:

Contributor A: 41% - 48%
Contributor B: 40% - 48%
allocation_recommendation: equalized_allocation

The updated assessment may supersede the original one.

Example: Structural Lineage Dispute

Initial assessment:

Contributor A: 45% - 55%

Evidence includes:

KSD record
Structure Fingerprint
Trace Protocol record

Another contributor challenges the lineage:

The structure is common in the field and should not be attributed only to A.

Dispute Registry records:

dispute_type: structural_lineage_challenge
counter_evidence: common_structure_claim
status: under_review

Possible outcome:

A's tolerance band widens.
Part of the allocation is moved to common_culture_pool.
Example: Trace Path Dispute

Initial trace:

Work A → Work B

Initial assessment:

Contributor A: 35% - 45%

Challenge:

Contributor B claims Work B was independently created.

Dispute Registry may record:

dispute_type: trace_path_challenge
independent_invention_claim: true
status: open

Possible outcome:

trace_confidence decreases
dispute_risk increases
tolerance_band widens
allocation changes from automatic_allocation to deferred_allocation
Example: Signed Impact Attestation Dispute

Initial evidence includes a Signed Impact Attestation.

SIA claims Contributor A had major structural impact.

Another party challenges the attestation:

The evaluator had incomplete evidence.

Dispute Registry records:

dispute_type: attestation_challenge
challenged_attestation_id: sia-001
status: under_review

Possible outcome:

attestation weight reduced
evidence_strength decreases
review_required = true

This prevents signed claims from becoming unquestionable authority.

How Disputes Affect Tolerance Bands

A dispute may affect several fields.

{
  "dispute_risk": 0.76,
  "review_required": true,
  "review_reasons": [
    "high_dispute_risk",
    "counter_evidence_present"
  ]
}

Disputes may:

widen the tolerance band
lower confidence
lower trace confidence
lower evidence strength
reduce estimator agreement
move a contributor to a different layer
change allocation recommendation
defer allocation
route value into a disputed pool
supersede the original assessment
Disputed Pool

If allocation cannot safely proceed, value may be placed into a disputed pool.

Example:

allocation_recommendation: deferred_allocation
pool_type: disputed_pool

This prevents premature distribution while preserving the possibility of later allocation.

A disputed pool may be used when:

evidence is contested
ranges are unstable
claimants disagree
high-value allocation is involved
dispute outcome may materially change distribution
Relationship to Suggested Distribution

Contribution Tolerance Band Model may propose a distribution.

Example:

{
  "recipient_id": "contributor_A",
  "allocation_share": 0.42,
  "allocation_type": "individual"
}

If this distribution is challenged, Dispute Registry records the dispute.

The allocation may then be:

reaffirmed
corrected
suspended
superseded
partially redirected
moved into a disputed pool
moved into a common culture pool
Relationship to Assessment Status

The assessment_status field may change based on dispute state.

Possible statuses:

draft
active
review_required
disputed
superseded
revoked
archived

Example flow:

draft
  ↓
active
  ↓
disputed
  ↓
superseded

Another possible flow:

active
  ↓
disputed
  ↓
reaffirmed externally
  ↓
active

Dispute Registry provides the record of why the status changed.

Relationship to Finality

Contribution assessments should rarely be treated as absolutely final.

A governance layer may classify finality as:

provisional
reviewed
disputed
settled
superseded
non_final

Dispute Registry helps track movement between these states.

This is important because new evidence may appear later.

A mature system should allow correction without destroying audit history.

Dispute Registry Record Reference

A Contribution Tolerance Band assessment may reference dispute records:

{
  "relationships": {
    "dispute_registry_record_ids": [
      "dispute-record-001"
    ]
  }
}

This allows later systems to see that the contribution assessment has been challenged, reviewed, or superseded.

Suggested Dispute Types

Dispute Registry may classify disputes such as:

range_overlap_conflict
estimated_value_challenge
tolerance_band_challenge
evidence_strength_challenge
trace_path_challenge
structural_lineage_challenge
independent_invention_claim
attestation_challenge
allocation_recommendation_challenge
contributor_exclusion_claim
contributor_inclusion_challenge
review_process_challenge

These categories help standardize dispute handling.

Dispute Outcomes

Possible outcomes include:

reaffirmed
corrected
superseded
revoked
partially_accepted
rejected
deferred
escalated
pooled
common_culture_pool_routing
no_action

A dispute outcome should not erase the previous record.

It should reference and explain it.

Supersession

Supersession is especially important.

When a contribution assessment is updated due to new evidence or dispute outcome, the new record should not silently replace the old one.

Instead:

old assessment → superseded_by → new assessment

Example:

{
  "assessment_status": "superseded",
  "relationships": {
    "dispute_registry_record_ids": [
      "dispute-record-001"
    ]
  }
}

The new assessment should reference the reason for the update.

Revocation

In rare cases, an assessment may be revoked.

Revocation may occur when:

evidence is found to be fraudulent
trace records were manipulated
attestation was invalid
contributor identity was incorrect
allocation was based on false claims

Revocation should be recorded transparently.

It should not simply delete history.

Reaffirmation

A dispute may also result in reaffirmation.

This means the original assessment remains valid after review.

Example:

Dispute filed
Evidence reviewed
Original contribution range reaffirmed

Reaffirmation is important because it protects valid assessments from repeated weak challenges.

Appeals

Some systems may allow appeal.

Appeal may be appropriate when:

new evidence appears
review process was incomplete
conflict of interest is alleged
estimator output was materially flawed
procedural error occurred

Appeals should be recorded as separate events, not hidden edits.

Relationship to Evidence Bundles

Counter-evidence should be included in the evidence bundle when relevant.

Example:

{
  "evidence": {
    "counter_evidence": [
      {
        "evidence_id": "counter-001",
        "evidence_type": "dispute_record",
        "description": "Counter-evidence challenging the claimed structural lineage.",
        "strength": 0.62,
        "confidence": 0.70
      }
    ]
  }
}

Counter-evidence may increase:

dispute risk
structure ambiguity
trace uncertainty
estimator variance

It may decrease:

confidence
evidence strength
allocation readiness
Relationship to Allocation Readiness

Dispute Registry strongly affects Allocation Readiness.

A case may not be allocation-ready if:

open dispute exists
counter-evidence exists
trace path is challenged
structural lineage is challenged
high-value allocation is contested
review outcome is pending

A case may become allocation-ready after:

dispute resolved
assessment reaffirmed
assessment corrected
allocation recommendation updated
pooled allocation accepted
common culture pool routing accepted
Relationship to Royalty OS

Royalty OS should use Dispute Registry to decide whether allocation can proceed.

If a contribution assessment is disputed, Royalty OS may:

pause allocation
route funds to a disputed pool
apply provisional allocation
require human review
update distribution after resolution
record supersession
refuse automatic allocation

This protects Royalty OS from distributing value based on unstable contribution claims.

Relationship to Trace Protocol

Trace Protocol may provide disputed trace records.

A trace dispute may occur when:

a trace path is denied
access history is incomplete
provenance conflicts with claimed lineage
trace records were added retroactively
independent invention is plausible

Dispute Registry records the challenge.

Contribution Tolerance Band Model adjusts uncertainty accordingly.

Relationship to KSD / Structure Fingerprint

KSD or Structure Fingerprint may be disputed when:

structural similarity is too generic
independent invention is plausible
another origin claim exists
the structure is common knowledge
lineage inference is overextended

Dispute Registry records the challenge.

Contribution Tolerance Band Model may widen the band or route the case to review.

Relationship to Signed Impact Attestation

Signed Impact Attestation may be disputed when:

evaluator bias is alleged
evidence was incomplete
attestation scope was unclear
attestation conflicts with trace records
newer evidence supersedes the claim

Dispute Registry allows attestations to be challenged without erasing them.

An attestation remains part of the audit trail, but its weight may change.

Anti-Abuse Role

Dispute Registry also helps prevent abuse.

Possible abuse includes:

false contribution claims
trace manipulation
spam disputes
repeated bad-faith challenges
coordinated attribution attacks
artificial range inflation
evidence flooding
retroactive claim insertion

Dispute Registry can help identify patterns of abuse.

However, it should also avoid becoming a tool for harassment.

A mature dispute system should protect both:

right to challenge
right to stability
Bad-Faith Disputes

Not all disputes are valid.

A bad-faith dispute may be:

repetitive
unsupported
retaliatory
spam-like
strategically timed
designed to delay allocation
used to intimidate contributors

Such disputes should be recorded, filtered, and weighted appropriately.

Possible handling:

rejected
no_action
rate_limited
requires_evidence
reviewer_flagged

This protects the system from endless contestation.

Provisional Allocation

Some systems may allow provisional allocation during dispute.

Example:

80% released
20% held in disputed pool

This may be useful when:

most evidence is stable
only a small portion is disputed
contributors agree to provisional handling
delaying all allocation would be unfair

Contribution Tolerance Band Model can help identify which portion is stable and which portion should be held.

Common Culture Pool After Dispute

A dispute may reveal that no individual claim is strong enough.

In that case, value may be routed to a common culture pool.

This may happen when:

the structure is broadly shared
origin cannot be determined
multiple plausible origins exist
evidence remains too weak
independent invention is likely
cultural diffusion is stronger than individual lineage

This prevents forced attribution where evidence does not justify it.

Minimal Integration Pattern
Contribution Tolerance Band assessment
+ evidence bundle
+ trace records
+ KSD records
+ signed attestations
+ counter-evidence
        ↓
Dispute Registry record
        ↓
review outcome
        ↓
updated assessment status
        ↓
Royalty OS allocation policy
Example End-to-End Flow
1. Contribution Tolerance Band Model estimates:
   Contributor A: 42% - 50%
   Contributor B: 39% - 47%

2. The model recommends pooled_allocation.

3. Contributor B disputes the assessment.

4. Dispute Registry records the dispute.

5. Additional evidence is reviewed.

6. The original assessment is corrected:
   Contributor A: 40% - 48%
   Contributor B: 41% - 49%

7. Allocation recommendation changes to equalized_allocation.

8. The old assessment is marked superseded.

9. The new assessment references the dispute record.

10. Royalty OS proceeds based on the updated assessment.
What Dispute Registry Should Not Do

Dispute Registry should not:

calculate contribution scores by itself
replace Contribution Tolerance Band Model
replace Royalty OS
determine legal ownership
erase prior records silently
treat every complaint as valid
allow endless bad-faith disputes
force automatic allocation
hide uncertainty

Dispute Registry records and governs contested claims.

It does not replace the assessment model.

Governance Benefits

By integrating Dispute Registry, the system gains:

transparent dispute history
safer allocation decisions
better auditability
correction without deletion
supersession tracking
counter-evidence handling
reduced false finality
better protection against abuse
more legitimate contribution assessment
Non-Goals

This document does not define the full Dispute Registry specification.

It does not define legal dispute resolution.

It does not replace courts, contracts, or copyright law.

It does not guarantee that all disputes will be resolved.

It only explains how Dispute Registry interacts with Contribution Tolerance Band Model.

Summary

Contribution Tolerance Band Model makes uncertainty visible.

Dispute Registry governs what happens when that uncertainty is challenged.

Together, they prevent two dangerous extremes:

false precision without review
endless dispute without structure

The core rule is:

A disputed contribution assessment should not disappear, harden prematurely, or be silently overwritten.

It should be recorded, reviewed, and, when necessary, corrected or superseded.

This allows royalty and attribution systems to remain flexible, auditable, and fair under imperfect evidence.
