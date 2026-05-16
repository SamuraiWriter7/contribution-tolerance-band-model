# Temporal Adjustment Notes

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Band Width Function, Model Weighting, Allocation Readiness, Review Status, Dispute Registry, Trace Protocol, KSD, Structure Fingerprint

---

## One-Line Summary

Temporal Adjustment Notes define how contribution estimates, tolerance bands, confidence, and allocation readiness may change over time.

Contribution is not always static.

Evidence may strengthen, weaken, diffuse, or become disputed as time passes.

---

## Why Temporal Adjustment Matters

Contribution assessments are usually created at a specific moment.

However, the evidence environment may change later.

New evidence may appear.

Old records may become stale.

A trace path may become clearer.

A dispute may be resolved.

A once-distinct structure may become common.

A contribution may become culturally diffused.

Because of this, a Contribution Tolerance Band assessment should not always be treated as permanently fixed.

Temporal Adjustment provides a way to handle time-based change without erasing audit history.

---

## Core Principle

Contribution assessments may change over time, but prior records should not be silently overwritten.

The system should preserve:

```text
original assessment
updated assessment
reason for change
timestamp of change
evidence used
review or dispute status
supersession relation

The goal is not to make contribution unstable.

The goal is to allow responsible updates when evidence changes.

Basic Relationship
Initial Contribution Assessment
        ↓
Time Passes
        ↓
Evidence Changes / Trace Changes / Dispute Changes
        ↓
Temporal Adjustment
        ↓
Updated Assessment or Supersession

Temporal Adjustment connects time to governance.

What Can Change Over Time

The following fields may change over time:

estimated_value
tolerance_band
lower_bound
upper_bound
confidence
evidence_strength
trace_confidence
estimator_agreement
dispute_risk
contribution_layer
allocation_recommendation
assessment_status
governance.finality_level

Not every change requires a new assessment.

But significant changes should usually create a superseding record.

What Should Not Change Silently

The following should not be silently edited without audit history:

contributor_id
target_work_id
original evidence records
prior contribution range
prior allocation recommendation
prior dispute status
prior review outcome

If these change, the old record should remain visible.

Temporal Factors

Temporal Adjustment may consider:

evidence_age
trace_age
record_stability
derivative_distance
cultural_diffusion
dispute_resolution
new_evidence
counter_evidence
provenance_decay
lineage_clarification
Evidence Age

Evidence age measures how old the supporting evidence is.

Old evidence is not automatically weak.

A timestamped publication record may remain strong for years.

However, old evidence may require review if:

the record source disappears
metadata becomes unverifiable
provenance chain breaks
newer counter-evidence appears
the field’s context changes

Effect:

stable old evidence → may remain strong
stale or unverifiable evidence → may increase uncertainty
Trace Age

Trace age measures how old a trace path is.

A trace path may remain reliable if it is well-preserved.

But trace confidence may decrease when:

links break
source records disappear
repository history is rewritten
intermediate records are missing
derivative chains become too long
provenance cannot be verified

Effect:

verified trace over time → stable or stronger confidence
broken trace over time → higher trace_uncertainty
Record Stability

Record stability measures whether the underlying records remain consistent.

Stable records include:

signed attestations
archived publication records
immutable logs
versioned repository history
preserved provenance metadata
verified audit logs

Unstable records include:

editable pages without history
deleted sources
unverifiable screenshots
unarchived claims
inconsistent metadata

Effect:

higher record_stability → narrower tolerance_band
lower record_stability → wider tolerance_band
Derivative Distance

Derivative distance measures how many transformation steps exist between the origin and the target work.

Example:

Origin Work
  ↓
Derivative A
  ↓
Derivative B
  ↓
Derivative C

As derivative distance increases, uncertainty may increase.

This is especially true when intermediate traces are weak.

Effect:

short derivative distance → stronger trace confidence
long derivative distance → higher temporal_uncertainty

However, long distance does not eliminate contribution.

It means the system should be more cautious.

Cultural Diffusion

Cultural diffusion occurs when an idea, structure, or pattern spreads widely.

Over time, a once-distinct contribution may become part of a broader field.

Example:

specific protocol pattern
  ↓
repeated adoption
  ↓
common design convention

When this happens, individual attribution may become harder.

Possible outcomes:

wider tolerance_band
shared_influence_layer
common_culture_pool
reduced individual allocation confidence

This protects the system from over-assigning broad cultural influence to one actor.

Lineage Clarification

Sometimes time strengthens contribution claims.

New evidence may clarify lineage.

Examples:

an old repository is discovered
an archived post confirms an origin date
a trace path is verified
a signed attestation is added
an independent review confirms structure
a dispute outcome reaffirms the assessment

Effect:

lineage clarified → tolerance_band may narrow
confidence may increase
allocation_readiness may improve

Time does not only weaken evidence.

It can also strengthen it.

Counter-Evidence Over Time

New counter-evidence may appear after an assessment.

Examples:

earlier origin record is discovered
independent invention evidence appears
trace manipulation is found
an attestation is challenged
KSD lineage is disputed
provenance conflict is identified

Effect:

counter_evidence appears
→ dispute_risk increases
→ tolerance_band widens
→ review_required or disputed

Significant counter-evidence should usually create a new assessment or Dispute Registry record.

Dispute Resolution Over Time

Disputes may change temporal status.

An open dispute may increase uncertainty.

A resolved dispute may reduce uncertainty.

Example:

open dispute
→ higher dispute_risk
→ wider band
→ allocation deferred

After resolution:

dispute reaffirmed original assessment
→ dispute_risk decreases
→ confidence increases
→ assessment may become active

or:

dispute corrected the assessment
→ old record superseded
→ new record becomes active or review_required
Temporal Uncertainty

Temporal uncertainty represents time-based instability.

Possible causes:

long derivative chains
stale evidence
missing intermediate traces
cultural diffusion
unresolved disputes
new counter-evidence
weak provenance preservation

In JSON-like terms:

{
  "uncertainty_factors": {
    "temporal_uncertainty": 0.25
  }
}

Higher temporal uncertainty should usually widen the tolerance band.

Minimal Temporal Adjustment Model

A simple conceptual model:

temporal_uncertainty =
  evidence_age_factor
+ trace_age_factor
+ derivative_distance_factor
+ cultural_diffusion_factor
+ unresolved_dispute_factor
- record_stability_factor
- lineage_clarification_factor

This is not a mandatory formula.

It is a conceptual guide.

Temporal Effect on Tolerance Band

Temporal uncertainty may feed into the Band Width Function.

Example:

epsilon =
  base_uncertainty
+ structure_ambiguity
+ trace_uncertainty
+ estimator_variance
+ dispute_risk
+ temporal_uncertainty
- evidence_strength

Suggested interpretation:

higher temporal_uncertainty → wider tolerance_band
lower temporal_uncertainty → narrower tolerance_band
Temporal Decay

Temporal decay means confidence may decrease over time when records are weak or missing.

However, decay should not be automatic for all records.

Good rule:

Time alone should not weaken a claim.
Time weakens a claim when preservation, traceability, or context becomes unstable.

This avoids unfairly penalizing older but well-documented contributions.

Suggested Temporal Decay Logic

A minimal decay model:

if record_stability is high:
    temporal_decay = low

if trace path is preserved:
    temporal_decay = low

if evidence source is missing:
    temporal_decay = moderate

if derivative distance is high and trace is weak:
    temporal_decay = high

if cultural diffusion is high:
    individual attribution confidence may decrease
Temporal Strengthening

Time can also strengthen assessment.

This may happen when:

additional evidence appears
a dispute is resolved
trace records are verified
independent review supports the claim
provenance is confirmed
structure lineage becomes clearer

Effect:

evidence_strength increases
trace_confidence increases
dispute_risk decreases
tolerance_band narrows
allocation_readiness improves

Temporal adjustment must allow strengthening as well as decay.

Example: Band Narrows Over Time

Initial assessment:

Contributor A: 35% - 55%

Later evidence:

archived publication record found
trace path verified
KSD lineage confirmed

Updated assessment:

Contributor A: 42% - 50%

Outcome:

tolerance_band narrowed
confidence increased
allocation_readiness improved
Example: Band Widens Over Time

Initial assessment:

Contributor A: 42% - 50%

Later evidence:

trace path disputed
alternative origin claim appears
intermediate records missing

Updated assessment:

Contributor A: 30% - 58%

Outcome:

tolerance_band widened
dispute_risk increased
review_required = true
Example: Cultural Diffusion

Initial assessment:

Contributor A: 45% - 55%

After broad adoption:

many independent systems adopt similar structure
origin becomes difficult to distinguish
pattern becomes common field convention

Updated handling:

Contributor A: 25% - 40%
Shared Influence Layer: increased
Common Culture Pool: activated

Outcome:

individual attribution confidence decreases
shared influence handling increases

This does not erase the origin.

It recognizes that the structure has become culturally diffused.

Example: Dispute Resolution

Initial assessment:

Contributor A: 42% - 50%
Contributor B: 39% - 47%
assessment_status = disputed

Dispute outcome:

B's implementation contribution is confirmed
A's origin contribution is reaffirmed

Updated assessment:

Contributor A: 40% - 48%
Contributor B: 40% - 48%
allocation_recommendation = equalized_allocation

Outcome:

old assessment = superseded
new assessment = active
Temporal States

A contribution assessment may have temporal states.

fresh
stable
stale
clarified
diffused
contested
superseded
archived
fresh

Use when the assessment is newly created and evidence is recent.

Risk:

may not yet have enough review history

Possible handling:

governance.finality_level = provisional
stable

Use when the assessment has remained consistent over time.

Indicators:

no open disputes
records remain verifiable
trace paths remain intact
estimator agreement remains high
no major counter-evidence appears

Possible handling:

allocation_readiness may increase
stale

Use when supporting records may be outdated or incomplete.

Indicators:

links broken
records missing
trace path not recently verified
repository history unclear
provenance unavailable

Possible handling:

review recommended
trace verification requested
clarified

Use when later evidence strengthens the assessment.

Indicators:

new trace evidence
verified provenance
resolved dispute
stronger KSD lineage
additional attestation

Possible handling:

confidence increases
tolerance_band narrows
diffused

Use when the contribution has spread into a broader field.

Indicators:

many derivatives exist
structure becomes common
origin attribution becomes harder
multiple sources plausibly influence later works

Possible handling:

shared_influence_layer
common_culture_pool
reduced individual allocation precision
contested

Use when the assessment becomes challenged over time.

Indicators:

dispute filed
counter-evidence appears
trace challenged
KSD lineage challenged
attestation challenged

Possible handling:

assessment_status = disputed
route to Dispute Registry
superseded

Use when a newer assessment replaces the old one.

Important rule:

Do not delete the old record.

The old record should remain part of the audit trail.

archived

Use when the record is preserved for historical reference.

Archived records may still be useful for:

audit
research
lineage history
governance review

But they should not drive active allocation unless reactivated by policy.

Suggested Temporal Metadata

A future schema version may include:

{
  "temporal_adjustment": {
    "temporal_state": "stable",
    "last_reviewed_at": "2026-05-17T00:00:00Z",
    "evidence_age_score": 0.18,
    "trace_age_score": 0.20,
    "record_stability": 0.82,
    "derivative_distance": 2,
    "cultural_diffusion_score": 0.25,
    "temporal_uncertainty": 0.16,
    "temporal_adjustment_note": "Trace path remains verifiable and no counter-evidence has appeared."
  }
}

For v0.1, temporal factors can be recorded in notes or uncertainty factors.

Suggested Future Fields

Possible future fields:

temporal_adjustment.temporal_state
temporal_adjustment.last_reviewed_at
temporal_adjustment.evidence_age_score
temporal_adjustment.trace_age_score
temporal_adjustment.record_stability
temporal_adjustment.derivative_distance
temporal_adjustment.cultural_diffusion_score
temporal_adjustment.temporal_uncertainty
temporal_adjustment.temporal_adjustment_note
Relationship to Band Width Function

Temporal uncertainty may be an input to the Band Width Function.

Example:

higher temporal_uncertainty
→ wider tolerance_band
→ review may be required

Lineage clarification may have the opposite effect.

Example:

new evidence appears
→ evidence_strength increases
→ tolerance_band narrows
Relationship to Model Weighting

Model weights may change over time.

Example:

early stage:
human_reviewer and structure_estimator may be more important

later stage:
provenance_estimator and trace_estimator may become stronger if records are verified

disputed stage:
dispute_aware_estimator and human_reviewer may increase in weight

Temporal Adjustment should allow weighting profiles to change when the evidence environment changes.

Relationship to Allocation Readiness

Temporal changes affect Allocation Readiness.

Example:

stale records
→ lower readiness

clarified lineage
→ higher readiness

open dispute over time
→ disputed state

cultural diffusion
→ common_culture_pool_ready

Allocation Readiness should be recalculated when major temporal events occur.

Relationship to Review Status

Temporal events may trigger status changes.

Examples:

new evidence appears → review_required
dispute filed → disputed
new assessment created → superseded
records become stale → review_required
assessment no longer used → archived

Review Status should reflect temporal changes.

Relationship to Dispute Registry

Disputes are time-based events.

Dispute Registry should record:

when the dispute began
what assessment was challenged
what evidence existed at that time
what new evidence appeared
how the outcome changed the assessment
whether a superseding record was created

Temporal Adjustment should reference dispute outcomes when relevant.

Relationship to Trace Protocol

Trace Protocol records may age, break, strengthen, or be verified over time.

Temporal Adjustment should consider:

trace freshness
trace preservation
trace verification status
trace conflict
trace gap
trace continuity

A trace path that remains verifiable over time should be stronger than one that cannot be reconstructed.

Relationship to KSD / Structure Fingerprint

KSD and Structure Fingerprint may change temporal interpretation.

A structure may begin as distinctive and later become common.

A lineage may initially be unclear and later become verified.

Temporal Adjustment should consider both possibilities.

distinctive structure becomes common → cultural diffusion increases
unclear lineage becomes verified → structure ambiguity decreases
Relationship to Royalty OS

Royalty OS should not assume that old contribution assessments remain permanently allocation-ready.

It should consider:

whether records remain valid
whether disputes have appeared
whether new evidence supersedes old assessments
whether cultural diffusion has changed allocation logic
whether a prior assessment should be archived

Temporal Adjustment helps Royalty OS avoid stale allocation decisions.

Supersession Over Time

When temporal adjustment materially changes an assessment, a new record should supersede the old one.

Example:

assessment-v1
  ↓ superseded_by
assessment-v2

The old assessment should remain available.

The new assessment should explain:

what changed
why it changed
what evidence was added
what review or dispute occurred
whether allocation recommendation changed
Anti-Abuse Role

Temporal Adjustment helps prevent time-based abuse.

Possible abuse includes:

retroactive origin claims
delayed disputes timed to block allocation
deletion of evidence
link rot exploitation
artificial cultural diffusion claims
repeated re-opening of settled cases
stale evidence manipulation

Possible protections:

preserve audit trails
require evidence for reopening
track dispute timing
record supersession
use archived records
require review for retroactive claims
Bad Temporal Assumptions

Avoid these assumptions:

older evidence is always weaker
newer evidence is always stronger
popular diffusion erases origin
absence of trace means absence of influence
initial assessment is always final
later dispute is always valid

Temporal Adjustment should be evidence-sensitive, not time-blind.

Reopening Assessments

A closed or stable assessment may be reopened when:

strong new evidence appears
fraud is discovered
trace path is invalidated
major counter-evidence appears
dispute process allows appeal
prior review was procedurally flawed

Reopening should require reasons.

Bad-faith reopening should be discouraged.

Periodic Review

Some systems may require periodic review.

Suggested use cases:

high-value allocations
long-lived royalty streams
unresolved shared influence
rapidly evolving domains
known dispute risk
important lineage claims

Example policy:

high_value_distribution → review every 12 months
disputed_pool → review every 6 months
common_culture_pool → review only if new evidence appears

These intervals are policy choices, not mandatory rules.

Temporal Audit Trail

A temporal audit trail should preserve:

assessment_id
created_at
updated_at
reviewed_at
superseded_at
archived_at
dispute_event_ids
evidence_change_ids
previous_range
updated_range
reason_for_change

Without an audit trail, temporal adjustment becomes invisible rewriting.

What Temporal Adjustment Should Not Do

Temporal Adjustment should not:

erase prior records
automatically decay valid evidence
treat time as proof by itself
rewrite contribution history silently
reopen settled cases without reason
convert cultural diffusion into individual entitlement
ignore new counter-evidence
replace Dispute Registry
replace Allocation Readiness

It adjusts interpretation over time.

It does not govern the entire system by itself.

Design Philosophy

Contribution lives in time.

A contribution may begin as a question.
It may become a structure.
It may become a protocol.
It may become a convention.
It may become culture.

A mature contribution system must remember the origin without freezing the future.

Temporal Adjustment allows the model to bend with time without breaking its audit trail.

Summary

Temporal Adjustment Notes define how Contribution Tolerance Band assessments may change over time.

The core rule is:

Time should not erase contribution, but time may change how contribution is interpreted.

Good temporal adjustment makes the system:

more realistic
more auditable
more adaptable
more resistant to stale evidence
more resistant to retroactive manipulation
more compatible with dispute handling
more compatible with long-term Royalty OS allocation

Contribution is not only a number.

It is a trace moving through time.
