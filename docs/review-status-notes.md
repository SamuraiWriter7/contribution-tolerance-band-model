# Review Status Notes

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Allocation Readiness, Dispute Registry, Trace Protocol, KSD, Structure Fingerprint, Signed Impact Attestation

---

## One-Line Summary

Review Status Notes define how Contribution Tolerance Band assessments should express review state, review reasons, and transition paths.

Contribution Tolerance Band Model estimates contribution under uncertainty.  
Review Status Notes explain how that uncertainty should be reviewed, paused, corrected, reaffirmed, or escalated.

---

## Why Review Status Matters

Contribution assessment is not always ready for allocation.

A record may be:

- incomplete
- provisional
- contested
- under review
- awaiting evidence
- affected by counter-evidence
- dependent on human review
- superseded by a newer assessment
- stable enough for allocation
- routed to Dispute Registry

Without clear review status, systems may accidentally treat uncertain assessments as final.

Review Status prevents premature certainty.

---

## Core Principle

A contribution assessment should clearly state whether it is:

```text
ready
under review
disputed
deferred
superseded
revoked
archived

The system should not hide uncertainty.

It should make review state visible, machine-readable, and auditable.

Relationship to Contribution Tolerance Band Model

Contribution Tolerance Band Model may include fields such as:

{
  "assessment_status": "review_required",
  "review_required": true,
  "review_reasons": [
    "wide_tolerance_band",
    "low_estimator_agreement"
  ]
}

Review Status Notes define how these fields should be interpreted.

Recommended Assessment Status Values

The current schema supports the following assessment_status values:

draft
active
review_required
disputed
superseded
revoked
archived

Each status should be used carefully.

draft

Use draft when the assessment is still being prepared.

A draft assessment may have:

incomplete evidence
incomplete contributor list
preliminary estimated values
incomplete tolerance bands
unreviewed estimator outputs
no allocation recommendation yet

A draft should not trigger allocation.

Recommended behavior:

allocation = blocked
review = optional
status = provisional
active

Use active when the assessment is currently valid for its intended purpose.

An active assessment may be used for:

allocation guidance
pooled allocation
review planning
audit reference
downstream Royalty OS processing

However, active does not mean absolutely final.

It means the record is currently accepted under available evidence.

Recommended behavior:

allocation = allowed if Allocation Readiness permits
review = not required unless later challenged
status = current
review_required

Use review_required when the assessment cannot safely proceed without additional review.

Triggers may include:

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

Recommended behavior:

automatic_allocation = blocked
pooled_allocation = allowed only if policy permits
human_review = required
audit_log = required
disputed

Use disputed when a formal challenge exists.

A disputed assessment may involve:

challenged estimated value
challenged tolerance band
challenged contributor inclusion
challenged contributor exclusion
challenged trace path
challenged KSD lineage
challenged Signed Impact Attestation
challenged allocation recommendation
counter-evidence

Recommended behavior:

automatic_allocation = blocked
dispute_registry = required
allocation = deferred or placed into disputed_pool
status = contested
superseded

Use superseded when a newer assessment replaces the current one.

A superseded assessment should not be deleted.

It should remain part of the audit trail.

Recommended behavior:

allocation = use newer assessment
audit_history = preserve old assessment
relationship = old assessment → superseded_by → new assessment

Supersession may happen when:

new evidence appears
dispute outcome changes the assessment
estimator outputs are updated
contributor ranges are corrected
allocation recommendation changes
previous calculation was flawed
revoked

Use revoked when the assessment should no longer be considered valid.

Revocation may occur when:

evidence was fraudulent
trace records were manipulated
contributor identity was incorrect
signed attestation was invalid
assessment was based on false claims
severe procedural error occurred

Recommended behavior:

allocation = blocked
downstream use = blocked
audit_history = preserve
review = required before any replacement

Revocation should not silently erase records.

It should be recorded with reasons.

archived

Use archived when the assessment is no longer active but remains preserved for reference.

Archived records may include:

old drafts
historical assessments
replaced versions
inactive assessments
records no longer used for allocation

Recommended behavior:

allocation = not active
audit_reference = allowed
historical_reference = allowed
Review Required vs Disputed

review_required and disputed are related but not identical.

review_required

Use when the system itself detects instability.

Example:

The tolerance band is too wide.
disputed

Use when a party formally challenges the assessment.

Example:

Contributor B challenges Contributor A's range.

A record may move from review_required to disputed if a review issue becomes a formal challenge.

Recommended Review Reasons

The schema supports these review reasons:

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
wide_tolerance_band

Use when the contribution range is too broad for safe allocation.

Example:

Contributor A: 20% - 70%

Recommended handling:

review_required = true
allocation = deferred or pooled
low_evidence_strength

Use when available evidence is too weak.

Examples:

no direct citation
vague provenance
weak structural evidence
unsupported influence claim
missing publication record
incomplete repository history

Recommended handling:

request additional evidence
widen tolerance band
block automatic allocation
low_trace_confidence

Use when trace paths are incomplete, unclear, or unreliable.

Examples:

missing trace path
indirect trace only
inferred trace without support
trace records conflict
trace source is unreliable

Recommended handling:

increase trace_uncertainty
reduce readiness
review trace evidence
low_estimator_agreement

Use when different estimators disagree.

Example:

Structure Estimator: high contribution
Provenance Estimator: low contribution
Trace Estimator: uncertain
Human Reviewer: review recommended

Recommended handling:

widen tolerance band
trigger human review
avoid strict allocation
high_estimator_variance

Use when estimator outputs vary too widely.

Example:

Estimator A: 0.20
Estimator B: 0.55
Estimator C: 0.70

Recommended handling:

review methodology
inspect estimator assumptions
defer allocation if needed
high_dispute_risk

Use when the assessment is likely to be challenged.

Risk may increase when:

economic value is high
ranges overlap
claims conflict
contributor roles are unclear
prior disputes exist
evidence is weak
counter-evidence is expected

Recommended handling:

route to review
require audit trail
avoid automatic allocation
range_overlap_conflict

Use when contribution ranges overlap in a way that affects allocation.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

Recommended handling:

pooled_allocation
equalized_allocation
human_review

Overlap is not always a problem.

It becomes a problem when strict ranking is required.

high_value_distribution

Use when the allocation has significant economic or institutional impact.

Even if evidence is reasonably strong, high-value cases may require stricter review.

Recommended handling:

human_review_required = true
audit_log_required = true
allocation_may_be_provisional
counter_evidence_present

Use when evidence challenges the assessment.

Counter-evidence may include:

alternative origin claim
conflicting trace record
disputed KSD lineage
independent invention claim
invalidated attestation
manipulated provenance
contributor exclusion claim

Recommended handling:

dispute_risk increases
review_required = true
possible Dispute Registry routing
manual_review_requested

Use when a contributor, reviewer, maintainer, institution, or governance process requests review.

Recommended handling:

review_required = true
record request source
preserve audit trail
other

Use only when no existing reason fits.

If other is used, the record should include an explanatory note.

Recommended handling:

review_reasons = ["other"]
notes = "Explain the reason clearly."
Review Status Transitions

A typical lifecycle may look like:

draft
  ↓
active
  ↓
review_required
  ↓
active

A disputed lifecycle may look like:

active
  ↓
disputed
  ↓
superseded

A revoked lifecycle may look like:

active
  ↓
disputed
  ↓
revoked

A historical lifecycle may look like:

active
  ↓
superseded
  ↓
archived
Suggested Transition Table
From	To	Reason
draft	active	Assessment completed
draft	review_required	Missing or unstable evidence
active	review_required	New uncertainty detected
active	disputed	Formal challenge filed
review_required	active	Review resolved without change
review_required	disputed	Review becomes formal dispute
disputed	active	Assessment reaffirmed
disputed	superseded	New assessment replaces old one
disputed	revoked	Assessment invalidated
superseded	archived	Historical record retained
revoked	archived	Invalidated record retained for audit
Review Outcomes

A review may result in:

reaffirmed
corrected
superseded
revoked
deferred
pooled
equalized
escalated
no_action
reaffirmed

Use when the original assessment remains valid after review.

Effect:

assessment_status may return to active
dispute_risk may decrease
confidence may increase
corrected

Use when the assessment remains valid but requires adjustment.

Corrections may affect:

estimated value
tolerance band
contribution layer
evidence strength
trace confidence
allocation recommendation
review reasons

If correction is substantial, supersession is preferred.

superseded

Use when a new record replaces the old assessment.

Effect:

old record = superseded
new record = active or review_required

The old record should remain available.

revoked

Use when the assessment is invalid.

Effect:

allocation blocked
downstream use blocked
new assessment required if needed
deferred

Use when the review cannot reach a stable conclusion.

Effect:

allocation postponed
additional evidence requested
possible disputed_pool
pooled

Use when exact individual allocation is not justified, but group allocation is stable.

Effect:

individual precision reduced
shared pool or near-contributor pool used
equalized

Use when contributors are close enough that strict ranking is not justified.

Effect:

contributors in same layer receive equal treatment
escalated

Use when the review needs a higher governance process.

Escalation may go to:

Dispute Registry
human review board
legal review
maintainer decision
institutional review
no_action

Use when the review request is unsupported, irrelevant, or bad-faith.

Effect:

assessment remains unchanged
review request logged
Review Status and Allocation Readiness

Review status directly affects allocation readiness.

Example mapping:

Review Status	Allocation Readiness Effect
draft	not_ready
active	depends on readiness signals
review_required	review_required
disputed	disputed
superseded	use newer assessment
revoked	not_ready
archived	not active

A record should not be considered allocation-ready merely because it exists.

Review Status and Royalty OS

Royalty OS should respect review status.

Recommended behavior:

draft → no allocation
active → allocation allowed if readiness permits
review_required → block automatic allocation
disputed → route to Dispute Registry or disputed pool
superseded → use newer assessment
revoked → block allocation
archived → historical reference only
Review Status and Dispute Registry

Dispute Registry should be used when review becomes contested.

Example:

review_required
  ↓
formal challenge filed
  ↓
disputed
  ↓
Dispute Registry record created

Dispute Registry may later produce an outcome:

reaffirmed
corrected
superseded
revoked
deferred
Review Status and Trace Protocol

Trace-related review may occur when:

trace path is missing
trace path is disputed
trace source is unreliable
trace manipulation is suspected
trace confidence is below threshold
trace conflicts with provenance

Possible review reason:

low_trace_confidence

or:

counter_evidence_present
Review Status and KSD / Structure Fingerprint

KSD-related review may occur when:

structural similarity is too generic
structural lineage is disputed
independent invention is plausible
KSD evidence conflicts with trace records
structure ambiguity is too high

Possible review reason:

wide_tolerance_band

or:

counter_evidence_present
Review Status and Signed Impact Attestation

Attestation-related review may occur when:

attestation scope is unclear
evaluator bias is alleged
attestation conflicts with other records
attestation is based on incomplete evidence
attestation has been superseded

Possible review reason:

counter_evidence_present

or:

manual_review_requested
Review Notes

Review notes should be:

specific
concise
evidence-based
auditable
non-defamatory
linked to records where possible

Bad review note:

This seems suspicious.

Better review note:

Trace confidence is low because no direct trace path exists between the claimed origin record and the target work. Structural similarity is present but may reflect a common pattern.
Review Metadata

A future schema version may include explicit review metadata.

Example:

{
  "review": {
    "status": "review_required",
    "requested_by": "maintainer",
    "requested_at": "2026-05-17T00:00:00Z",
    "review_reasons": [
      "wide_tolerance_band",
      "low_estimator_agreement"
    ],
    "review_outcome": "pending",
    "review_notes": "Contributor ranges overlap and estimator outputs diverge.",
    "related_dispute_ids": []
  }
}

For v0.1, review state can be expressed through:

assessment_status
review_required
review_reasons
allocation_recommendation.review_required
allocation_recommendation.review_reasons
relationships.dispute_registry_record_ids
governance.finality_level
Bad-Faith Review Requests

Not all review requests are valid.

Bad-faith review requests may be:

repetitive
unsupported
retaliatory
spam-like
strategically timed
meant to delay allocation
meant to harass contributors

A mature system should preserve the right to challenge while protecting against abuse.

Possible handling:

no_action
requires_evidence
rate_limited
reviewer_flagged
bad_faith_pattern_logged
Review Stability

Review status should not change too easily.

If a record moves repeatedly between states, the system should detect instability.

Example:

active → disputed → active → disputed → active

This may indicate:

unresolved evidence conflict
bad-faith disputes
weak governance
unstable estimator outputs
unclear allocation policy

Recommended handling:

escalated review
stricter evidence requirements
temporary allocation hold
Provisional Review State

Some systems may allow provisional use.

Example:

assessment_status = active
governance.finality_level = provisional

This means the assessment may be used, but remains open to correction.

Provisional use should be clearly marked.

It should not be confused with final judgment.

Finality Levels

The governance.finality_level field may express:

provisional
reviewed
disputed
settled
superseded
non_final

Recommended meaning:

Finality Level	Meaning
provisional	usable but not final
reviewed	reviewed under current evidence
disputed	currently challenged
settled	resolved under the applicable governance process
superseded	replaced by newer record
non_final	not ready for final use
Auditability

All review transitions should be auditable.

A system should preserve:

previous status
new status
reason for transition
evidence used
reviewer or process reference
timestamp
related dispute record
superseding assessment if any

A review process that silently changes records weakens trust.

Minimal Integration Pattern
Contribution Tolerance Band assessment
        ↓
review_required / review_reasons
        ↓
Allocation Readiness
        ↓
review, dispute, allocation, deferral, or pooling
        ↓
updated assessment_status
        ↓
audit trail preserved
Example End-to-End Review Flow
1. Assessment is created as draft.

2. Evidence and estimator outputs are added.

3. Assessment becomes active.

4. Allocation Readiness detects overlapping ranges.

5. assessment_status becomes review_required.

6. Human review determines that pooled allocation is appropriate.

7. allocation_recommendation becomes pooled_allocation.

8. assessment_status returns to active.

9. Audit trail records the review outcome.
Example Dispute Flow
1. Assessment is active.

2. Contributor B challenges Contributor A's range.

3. assessment_status becomes disputed.

4. Dispute Registry record is created.

5. Counter-evidence is reviewed.

6. New assessment supersedes the old one.

7. Old assessment is marked superseded.

8. Royalty OS uses the new assessment.
What Review Status Should Not Do

Review Status should not:

replace contribution assessment
replace Allocation Readiness
replace Dispute Registry
erase evidence
silently overwrite history
treat every challenge as valid
allow endless bad-faith review loops
convert provisional assessments into final ones without process

Review Status is a state layer.

It does not determine contribution by itself.

Governance Benefits

Clear review status provides:

better auditability
safer allocation timing
clearer dispute routing
reduced false finality
better contributor trust
clearer lifecycle management
protection against premature allocation
protection against endless disputes
Non-Goals

This document does not define the full review governance process.

It does not define legal appeals.

It does not replace Dispute Registry.

It does not determine contribution ranges.

It only explains how review status should be expressed and interpreted in relation to Contribution Tolerance Band assessments.

Summary

Review Status Notes define how contribution assessments move through uncertainty.

They prevent a system from treating unstable records as final.

The core rule is:

A contribution assessment should always show whether it is draft, active, under review, disputed, superseded, revoked, or archived.

Clear review status turns uncertainty into governance.

Without it, tolerance bands may be misunderstood as final answers.

With it, they become part of a responsible allocation system.
