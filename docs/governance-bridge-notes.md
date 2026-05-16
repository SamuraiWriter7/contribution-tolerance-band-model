# Governance Bridge Notes

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Allocation Readiness, Review Status, Dispute Registry, Trace Protocol, KSD, Structure Fingerprint, Signed Impact Attestation

---

## One-Line Summary

Governance Bridge Notes define how Contribution Tolerance Band assessments move from uncertainty-aware scoring into review, allocation readiness, dispute handling, and Royalty OS policy.

This document connects the assessment layer to the governance layer.

---

## Why a Governance Bridge Is Needed

Contribution Tolerance Band Model estimates contribution under uncertainty.

However, estimation alone is not enough.

A system also needs to decide:

- whether the assessment can be used
- whether allocation may proceed
- whether review is required
- whether a dispute must be recorded
- whether value should be pooled
- whether allocation should be deferred
- whether a newer assessment should supersede an older one

Without a governance bridge, contribution ranges may be misused as final decisions.

Governance Bridge prevents that.

---

## Core Principle

A contribution range is not a final allocation decision.

It is an input to governance.

```text
Contribution Range
  ↓
Review Status
  ↓
Allocation Readiness
  ↓
Dispute Handling
  ↓
Royalty OS Allocation Policy

The bridge ensures that uncertainty is not ignored, hidden, or converted into false precision.

Layer Separation

Each layer has a different role.

Contribution Tolerance Band Model
  = estimates contribution as a range

Review Status
  = shows whether the assessment is draft, active, under review, disputed, superseded, revoked, or archived

Allocation Readiness
  = decides whether the assessment is stable enough to affect value distribution

Dispute Registry
  = records and governs contested assessments

Royalty OS
  = applies allocation policy

No layer should do everything.

This separation prevents brittle governance.

Governance Flow

A typical governance flow may look like this:

1. A target work is submitted.

2. Evidence is collected:
   - Trace Protocol records
   - KSD / Structure Fingerprint records
   - provenance records
   - Signed Impact Attestations
   - human review notes
   - counter-evidence if any

3. Contribution Tolerance Band Model estimates contribution ranges.

4. Review Status marks the assessment lifecycle state.

5. Allocation Readiness checks whether the assessment can affect allocation.

6. If stable, Royalty OS may allocate.

7. If unstable, the case may move to review, pooling, deferral, or Dispute Registry.

8. If new evidence appears, a new assessment may supersede the old one.
Governance States

A contribution assessment may pass through several governance states.

draft
active
review_required
disputed
allocation_ready
pooled_ready
deferred
superseded
revoked
archived

These states should be machine-readable and auditable.

Minimal State Mapping
Condition	Review Status	Readiness State	Recommended Governance Action
Incomplete record	draft	not_ready	Continue evidence collection
Narrow band + strong evidence	active	allocation_ready	Allow allocation
Overlapping credible ranges	active or review_required	pooled_ready	Use pooled allocation
Wide band	review_required	review_required	Human review or defer
Open dispute	disputed	disputed	Route to Dispute Registry
Weak evidence + unclear origin	review_required	common_culture_pool_ready	Route to common culture pool
Invalidated evidence	revoked	not_ready	Block allocation
Newer record exists	superseded	use newer assessment	Preserve old record for audit
Historical record only	archived	not active	Reference only
Governance Inputs

The bridge may use these inputs:

assessment_status
contribution ranges
tolerance_band width
evidence_strength
trace_confidence
estimator_agreement
estimator_variance
dispute_risk
review_required
review_reasons
allocation_recommendation
relationships.dispute_registry_record_ids
governance.finality_level
counter_evidence status
value_at_risk
Governance Outputs

The bridge may produce or recommend:

automatic_allocation
pooled_allocation
equalized_allocation
human_review
dispute_registry
deferred_allocation
common_culture_pool
disputed_pool
no_allocation
supersession_required
revocation_required
Bridge Rule 1: Do Not Allocate from Unstable Uncertainty

If a contribution range is too wide, weakly supported, or disputed, it should not directly trigger allocation.

Example:

Contributor A: 20% - 70%

Recommended handling:

review_required
deferred_allocation
human_review

The system should not pretend this range is stable.

Bridge Rule 2: Overlap Does Not Always Mean Failure

Overlapping ranges do not automatically block allocation.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

This may be handled through:

pooled_allocation
equalized_allocation
near_contributor_pool
human_review

Overlap becomes dangerous only when the system tries to force strict ranking without sufficient evidence.

Bridge Rule 3: Wider Uncertainty Should Not Mean Wider Entitlement

A broad contribution range should not automatically create a larger claim.

Example:

Contributor A: 10% - 90%

This does not mean Contributor A should receive a large allocation.

It means the system does not know enough.

Recommended handling:

not_ready
review_required
deferred_allocation
common_culture_pool

This rule prevents gaming.

Bridge Rule 4: Disputes Should Be Routed, Not Hidden

If an assessment is challenged, the challenge should be recorded.

A disputed assessment should not be silently overwritten.

Recommended handling:

assessment_status = disputed
relationships.dispute_registry_record_ids = [...]
allocation_recommendation.type = dispute_registry or deferred_allocation

Dispute is not system failure.

It is governance.

Bridge Rule 5: Supersession Should Preserve History

When a newer assessment replaces an older one, the older one should be marked as superseded.

It should not be deleted.

Example:

old assessment → superseded_by → new assessment

This preserves auditability.

Bridge Rule 6: Revocation Should Be Explicit

If an assessment is invalidated, it should be marked as revoked.

Revocation may occur when:

evidence was fraudulent
trace records were manipulated
contributor identity was incorrect
attestation was invalid
severe procedural error occurred

Revoked records should remain visible for audit, but should not be used for allocation.

Bridge Rule 7: Common Culture Pool Is a Governance Safety Valve

Some influence may be real but not individually attributable.

In such cases, forcing individual allocation may create false claims.

Common culture pool may be appropriate when:

origin is unclear
structure is broadly shared
multiple plausible origins exist
independent invention is plausible
contribution has become cultural rather than individual
evidence remains too weak for personal attribution

This prevents the system from over-assigning ownership.

Bridge Rule 8: High-Value Allocation Requires Stronger Governance

When value at risk is high, stricter thresholds should apply.

High-value cases may require:

narrower tolerance bands
stronger evidence
higher trace confidence
higher estimator agreement
lower dispute risk
human review
audit log
appeal process

Example:

high_value_distribution = true
review_required = true

This protects the system from costly misallocation.

Bridge Rule 9: Review Status Must Affect Allocation Readiness

Review status should not be decorative.

It must affect whether allocation can proceed.

Recommended mapping:

draft → not_ready
active → readiness check required
review_required → block automatic allocation
disputed → Dispute Registry or disputed pool
superseded → use newer assessment
revoked → block allocation
archived → reference only
Bridge Rule 10: Governance Must Be Auditable

Every meaningful state transition should be logged.

The audit trail should preserve:

previous status
new status
reason for transition
evidence used
reviewer or process reference
timestamp
related dispute record
superseding assessment if any

Governance without auditability becomes invisible power.

Auditability keeps the system accountable.

Example: Stable Allocation Flow
1. Assessment created:
   Contributor A: 55% - 60%
   Contributor B: 25% - 30%
   Contributor C: 10% - 15%

2. Evidence strength is high.

3. Trace confidence is high.

4. Dispute risk is low.

5. Review Status = active.

6. Allocation Readiness = allocation_ready.

7. Royalty OS proceeds with automatic_allocation.

8. Audit log records decision path.
Example: Pooled Allocation Flow
1. Assessment created:
   Contributor A: 42% - 50%
   Contributor B: 39% - 47%
   Contributor C: 12% - 18%

2. A and B ranges overlap.

3. Evidence is sufficient.

4. Dispute risk is low.

5. Allocation Readiness = pooled_ready.

6. Royalty OS uses pooled_allocation.

7. A/B are treated as near contributors rather than strictly ranked.
Example: Dispute Flow
1. Assessment is active.

2. Contributor B challenges Contributor A's range.

3. assessment_status becomes disputed.

4. Dispute Registry record is created.

5. Allocation is paused or moved to disputed_pool.

6. Review outcome changes the ranges.

7. New assessment supersedes the old one.

8. Royalty OS uses the updated assessment.
Example: Common Culture Pool Flow
1. Structural influence is detected.

2. KSD suggests similarity.

3. Trace evidence is weak.

4. Multiple possible origins exist.

5. Independent invention is plausible.

6. Allocation Readiness = common_culture_pool_ready.

7. Royalty OS routes value to common_culture_pool.
Example: Revocation Flow
1. Assessment is active.

2. Later evidence shows trace records were manipulated.

3. assessment_status becomes disputed.

4. Dispute Registry review confirms manipulation.

5. assessment_status becomes revoked.

6. Allocation is blocked.

7. Audit trail preserves the revoked assessment.
Relationship to Contribution Tolerance Band Model

Contribution Tolerance Band Model provides the assessment layer.

It produces:

estimated contribution value
tolerance band
lower and upper range
confidence
evidence strength
trace confidence
estimator agreement
dispute risk
allocation recommendation

Governance Bridge interprets whether those outputs are safe to use.

Relationship to Allocation Readiness

Allocation Readiness is the main gate.

Governance Bridge uses Allocation Readiness to determine whether the assessment can influence allocation.

Contribution Tolerance Band
        ↓
Allocation Readiness
        ↓
Royalty OS policy

If readiness is low, governance must prevent premature allocation.

Relationship to Review Status

Review Status gives the lifecycle state.

Governance Bridge uses it to prevent misinterpretation.

Example:

assessment_status = review_required

This should block automatic allocation unless policy explicitly allows provisional handling.

Relationship to Dispute Registry

Dispute Registry handles contested cases.

Governance Bridge routes cases to Dispute Registry when:

formal challenge exists
counter-evidence appears
dispute risk exceeds threshold
trace path is challenged
structural lineage is challenged
attestation is challenged
allocation recommendation is challenged

Dispute Registry then records the dispute lifecycle.

Relationship to Royalty OS

Royalty OS should not directly consume contribution ranges without governance checks.

It should consume:

contribution range
+ review status
+ allocation readiness
+ dispute status
+ governance finality

Only then should Royalty OS apply allocation policy.

Relationship to Trace Protocol

Trace Protocol supplies trace evidence.

Governance Bridge checks whether trace evidence is strong enough to support allocation.

Weak or disputed trace evidence should reduce readiness.

Relationship to KSD / Structure Fingerprint

KSD supplies structural evidence.

Governance Bridge checks whether the structural evidence is specific, supported, and non-generic enough for allocation use.

Generic or disputed structural evidence should trigger review or common culture pool routing.

Relationship to Signed Impact Attestation

Signed Impact Attestation supplies accountable claims.

Governance Bridge treats attestations as evidence, not final judgment.

A disputed or weak attestation may reduce allocation readiness.

A strong and aligned attestation may increase readiness.

Suggested Future JSON Object

A future schema version may include a governance_bridge object.

Example:

{
  "governance_bridge": {
    "state": "pooled_ready",
    "decision_basis": [
      "credible_overlapping_ranges",
      "sufficient_evidence_strength",
      "low_dispute_risk"
    ],
    "blocked_actions": [
      "strict_individual_ranking"
    ],
    "allowed_actions": [
      "pooled_allocation",
      "human_review"
    ],
    "recommended_next_step": "pooled_allocation",
    "audit_required": true
  }
}

For v0.1, this can be inferred from:

assessment_status
allocation_recommendation
review_required
review_reasons
relationships
governance.finality_level
Decision Table
Assessment Condition	Governance State	Recommended Action
Narrow band, strong evidence, low dispute risk	stable	automatic_allocation
Overlapping but credible ranges	pooled_ready	pooled_allocation
Wide band, weak evidence	unstable	human_review or deferred_allocation
Open dispute	contested	dispute_registry
Generic structure, unclear origin	diffuse	common_culture_pool
Manipulated evidence	invalid	revoked
Newer assessment exists	superseded	use newer assessment
Historical record only	archived	reference only
Anti-Abuse Role

Governance Bridge helps prevent abuse such as:

artificial range inflation
trace spam
fake provenance
weak but repeated claims
strategic disputes
retroactive attribution attempts
evidence flooding
false structural lineage claims
bad-faith review requests

The bridge should ensure that uncertainty does not become entitlement.

Bad-Faith Governance Risks

Governance itself can also be abused.

Risks include:

endless review loops
strategic dispute filing
biased reviewers
opaque moderation
arbitrary revocation
silent supersession
hidden allocation changes

Therefore, governance decisions must be logged, explainable, and appealable where appropriate.

Provisional Allocation

Some cases may allow provisional allocation.

Example:

80% released
20% held in disputed_pool

Provisional allocation may be useful when:

most evidence is stable
only part of the allocation is disputed
delaying all allocation would be unfair
correction is possible later
audit trails are preserved

Provisional allocation should always be clearly marked.

Governance Finality

Finality should be explicit.

Possible finality levels:

provisional
reviewed
disputed
settled
superseded
non_final

A record should not appear final if it remains open to review.

What Governance Bridge Should Not Do

Governance Bridge should not:

calculate contribution ranges by itself
replace Contribution Tolerance Band Model
replace Dispute Registry
replace Royalty OS
determine legal ownership
erase records silently
force automatic allocation
treat uncertainty as entitlement
treat all disputes as valid
block all allocation forever

It is a coordination layer.

It connects assessment, readiness, review, dispute, and allocation.

Minimal Integration Pattern
Contribution Tolerance Band assessment
+ Review Status
+ Allocation Readiness
+ Dispute Registry references
+ Governance finality
        ↓
Governance Bridge decision
        ↓
Royalty OS allocation policy
Design Philosophy

Governance should not freeze uncertainty too early.

It should not let uncertainty flow without control either.

It should behave like a bridge over moving water.

The water moves.

The bridge holds.

A mature contribution system needs both flexibility and structure.

Non-Goals

This document does not define the full governance system.

It does not replace legal process.

It does not enforce payment.

It does not define all Royalty OS policies.

It does not replace human review in high-risk cases.

It explains how Contribution Tolerance Band assessments should connect to governance and allocation layers.

Summary

Governance Bridge Notes connect the technical assessment layer to the institutional decision layer.

Contribution Tolerance Band Model makes uncertainty visible.

Review Status shows lifecycle state.

Allocation Readiness decides whether the assessment is stable enough to use.

Dispute Registry governs contested claims.

Royalty OS applies allocation policy.

The core rule is:

A contribution range should never become an allocation decision without governance.

This bridge keeps the system flexible, auditable, and resistant to false precision.
