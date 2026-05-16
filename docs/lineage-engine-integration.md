# Lineage Engine Integration

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Trace Protocol, KSD, Structure Fingerprint, Band Width Function, Model Weighting, Temporal Adjustment, Allocation Readiness, Dispute Registry, Governance Bridge

---

## One-Line Summary

Lineage Engine Integration defines how lineage records should connect to Contribution Tolerance Band assessments.

Lineage Engine identifies possible origin, derivation, adaptation, influence, or structural inheritance.  
Contribution Tolerance Band Model converts those lineage signals into uncertainty-aware contribution ranges.

---

## Why Lineage Engine Integration Matters

Contribution is not always a direct one-step relation.

A work may be connected through:

- origin
- derivation
- adaptation
- remix
- translation
- structural inheritance
- conceptual influence
- protocol reuse
- implementation extension
- indirect transformation
- multi-step lineage

Lineage Engine helps identify these relationships.

However, lineage alone should not determine contribution share.

A lineage relation is evidence.

It is not automatic allocation.

---

## Basic Relationship

```text
Lineage Engine
      ↓
Lineage Evidence
      ↓
Contribution Tolerance Band Model
      ↓
Contribution Range
      ↓
Allocation Readiness
      ↓
Royalty OS / Review / Dispute Handling

Lineage Engine answers:

How is this work related to previous works or contributors?

Contribution Tolerance Band Model answers:

How should that relationship affect contribution assessment under uncertainty?

What Lineage Engine Provides

Lineage Engine may provide records such as:

origin_candidate
derived_from
adapted_from
influenced_by
translated_from
remixed_from
implemented_from
extended_from
forked_from
conceptually_related_to
structurally_similar_to
unknown_or_uncertain_lineage

These records help describe how works, ideas, protocols, or structures may be connected.

Lineage Is Not Ownership

A lineage relation should not be treated as legal ownership.

Example:

Work B is influenced_by Work A.

This does not automatically mean:

Contributor A owns part of Work B.

Instead, the model should ask:

How strong is the lineage evidence?
How direct is the relation?
How specific is the structural inheritance?
Is the lineage disputed?
Is independent invention plausible?
What is the uncertainty band?

This prevents lineage systems from becoming overclaim systems.

Lineage Relation Types

A minimal lineage relation set may include:

origin_candidate
derived_from
adapted_from
influenced_by
translated_from
remixed_from
implemented_from
extended_from
forked_from
structurally_similar_to
conceptually_related_to
unknown

Each relation type should affect contribution assessment differently.

origin_candidate

Use origin_candidate when a source may be the original starting point.

Examples:

first known publication
earliest timestamped protocol
earliest structure record
original question
first public repository
first signed attestation

Effect:

may increase evidence_strength
may increase contribution estimate
may reduce structure_ambiguity if well-supported

Caution:

origin_candidate is not proof of absolute origin
derived_from

Use derived_from when a later work clearly builds on an earlier work.

Examples:

explicit derivative
documented reuse
visible transformation
repository fork
adapted schema
versioned continuation

Effect:

stronger lineage evidence
narrower tolerance band if trace is clear
higher allocation readiness if not disputed
adapted_from

Use adapted_from when a work modifies or recontextualizes an earlier work.

Examples:

simplified version
domain-specific adaptation
format conversion
explanatory rewrite
protocol adaptation
implementation variant

Effect:

moderate to strong contribution signal
requires transformation analysis
may support pooled or layered allocation
influenced_by

Use influenced_by when connection exists but derivation is indirect.

Examples:

conceptual influence
structural inspiration
thematic influence
indirect reuse of framework
non-explicit reference

Effect:

usually wider tolerance band
requires supporting trace, KSD, or review evidence

Caution:

influence alone should not create strong allocation rights
translated_from

Use translated_from when a work is translated from another work.

Effect:

source contributor may retain strong lineage claim
translator may receive transformation/editing contribution
allocation may require role separation

Possible layers:

originator
translator
editor
publisher
adapter
remixed_from

Use remixed_from when multiple sources are combined.

Example:

Work C remixes Work A and Work B.

Effect:

requires multi-source contribution assessment
range overlap is likely
pooled allocation may be appropriate
implemented_from

Use implemented_from when an abstract design, protocol, or specification becomes code or operational system.

Example:

Protocol specification → software implementation

Effect:

origin/design contributor and implementer should be separated
implementation contribution should not erase structural origin
structural origin should not erase implementation work

This relation is especially important for Royalty OS and protocol repositories.

extended_from

Use extended_from when a later work adds substantial new components to an earlier structure.

Effect:

earlier contributor may retain lineage contribution
later contributor may receive extension contribution
tolerance bands may separate origin and extension layers
forked_from

Use forked_from when a repository, project, or specification branches from another.

Effect:

strong provenance evidence if repository history is clear
requires analysis of new contribution added after fork

Fork does not automatically mean equal contribution.

It indicates a traceable relationship.

structurally_similar_to

Use structurally_similar_to when works share a structural pattern but direct lineage is uncertain.

Effect:

structure_ambiguity may remain high
tolerance_band should usually widen
review may be required

Caution:

structural similarity is evidence, not final proof
conceptually_related_to

Use conceptually_related_to when works share a concept, theme, or problem framing.

Effect:

weak to moderate evidence
usually insufficient for allocation without additional support

This relation should be handled carefully to avoid overclaim.

unknown

Use unknown when lineage cannot be determined.

Effect:

wide tolerance band
low allocation readiness
possible common_culture_pool
possible deferred_allocation
Lineage Strength

Lineage strength measures how strong the relationship appears to be.

Possible levels:

strong
moderate
weak
unclear
disputed
Strong Lineage

Indicators:

explicit reference
timestamped origin
clear trace path
repository history
direct derivation
matching structure fingerprint
supporting attestation

Effect:

higher evidence_strength
lower trace_uncertainty
narrower tolerance_band
Moderate Lineage

Indicators:

meaningful structural similarity
partial trace path
incomplete provenance
indirect reference
human review support

Effect:

moderate tolerance band
review may be useful
Weak Lineage

Indicators:

thematic similarity only
missing trace
generic structure
unclear origin
multiple possible sources

Effect:

wide tolerance band
automatic allocation should be avoided
Disputed Lineage

Indicators:

counter-evidence
independent invention claim
conflicting origin records
challenged trace path
challenged KSD record

Effect:

review_required
possible Dispute Registry routing
Lineage Confidence

Lineage confidence measures how reliable the lineage claim is.

Example:

{
  "lineage_confidence": 0.78
}

High confidence means the relation is well-supported.

Low confidence means the relation is uncertain.

Lineage confidence may be derived from:

trace_confidence
evidence_strength
structure_specificity
provenance_quality
estimator_agreement
dispute_risk
Lineage vs Trace

Lineage and trace are related but not identical.

Trace

Trace records the path.

Example:

Work A → Work B
Lineage

Lineage interprets the relationship.

Example:

Work B is adapted_from Work A.

Trace is connection.

Lineage is relationship type.

Contribution Tolerance Band Model needs both.

Lineage vs Structure Fingerprint

Structure Fingerprint identifies structural similarity or continuity.

Lineage Engine interprets whether that similarity may represent:

derivation
adaptation
influence
common structure
independent invention
unknown relation

Structure Fingerprint supplies signals.

Lineage Engine classifies relation.

Contribution Tolerance Band Model estimates uncertainty-aware contribution.

Lineage vs Allocation

Lineage should not directly allocate value.

Unsafe pattern:

Lineage detected
→ automatic royalty share

Safer pattern:

Lineage detected
→ contribution range estimated
→ allocation readiness checked
→ governance applied
→ Royalty OS allocates if safe

This separation is essential.

Suggested Integration Flow
1. Target work is submitted.

2. Trace Protocol identifies trace records.

3. KSD / Structure Fingerprint identifies structural signals.

4. Lineage Engine classifies possible relationships.

5. Contribution Tolerance Band Model estimates contribution ranges.

6. Band Width Function adjusts uncertainty.

7. Model Weighting combines estimator outputs.

8. Allocation Readiness checks whether the result can affect allocation.

9. Dispute Registry handles contested claims.

10. Royalty OS applies allocation policy.
Lineage Evidence in JSON

Lineage evidence may appear in the evidence bundle.

Example:

{
  "evidence": {
    "structural_evidence": [
      {
        "evidence_id": "ev-lineage-001",
        "evidence_type": "conceptual_lineage",
        "source_id": "lineage-record-001",
        "description": "Lineage Engine classifies the target protocol as adapted_from the earlier structure.",
        "strength": 0.76,
        "confidence": 0.72
      }
    ]
  }
}

The current schema supports conceptual_lineage as an evidence type.

Future versions may add explicit lineage fields.

Suggested Future Schema Extension

A future schema version may include a lineage object.

Example:

{
  "lineage": {
    "lineage_record_id": "lineage-2026-0001",
    "relation_type": "adapted_from",
    "source_work_id": "work-origin-001",
    "target_work_id": "work-target-001",
    "lineage_strength": "moderate",
    "lineage_confidence": 0.72,
    "lineage_evidence_ids": [
      "ev-lineage-001",
      "ev-trace-001",
      "ev-structure-001"
    ],
    "independent_invention_possible": false,
    "disputed": false,
    "lineage_note": "Target work adapts the origin structure into a protocol-level schema."
  }
}

For v0.1, lineage information can be represented through evidence bundles, relationship IDs, and notes.

Suggested Future Fields

Possible future fields:

lineage.lineage_record_id
lineage.relation_type
lineage.source_work_id
lineage.target_work_id
lineage.lineage_strength
lineage.lineage_confidence
lineage.lineage_evidence_ids
lineage.independent_invention_possible
lineage.disputed
lineage.lineage_note
Lineage and Band Width Function

Lineage affects tolerance band width.

Strong lineage may narrow the band.

Weak or disputed lineage may widen the band.

Example:

strong derived_from relation
+ clear trace
+ strong structure fingerprint
= narrower tolerance_band

Example:

structurally_similar_to
+ missing trace
+ independent invention possible
= wider tolerance_band

Lineage should feed into:

structure_ambiguity
trace_uncertainty
evidence_strength
dispute_risk
Lineage and Model Weighting

Lineage Engine may be treated as an estimator or evidence source.

Possible estimator:

lineage_estimator

It may evaluate:

relation type
relation strength
derivative distance
source-target connection
independent invention risk
dispute status

Suggested weight:

0.10 - 0.30

In structure-heavy cases, lineage estimator weight may increase.

In disputed cases, lineage estimator should be balanced with provenance and human review.

Lineage and Temporal Adjustment

Lineage may change over time.

A relation may become clearer when new evidence appears.

A relation may weaken when independent invention evidence appears.

A relation may become diffused when a structure becomes common.

Examples:

unclear lineage → clarified lineage
direct lineage → disputed lineage
specific lineage → culturally diffused influence

Temporal Adjustment should preserve old lineage interpretations and record updated ones.

Lineage and Allocation Readiness

Lineage strength affects allocation readiness.

Possible mapping:

Lineage Condition	Allocation Readiness Effect
Strong + supported lineage	readiness increases
Moderate lineage	review may be useful
Weak lineage	readiness decreases
Disputed lineage	disputed or review_required
Unknown lineage	deferred or common_culture_pool
Generic structural relation	common_culture_pool or review

Lineage alone should not create allocation readiness.

It must be combined with evidence strength, trace confidence, estimator agreement, and dispute risk.

Lineage and Dispute Registry

Lineage disputes should be recorded.

Possible disputes:

origin_candidate_challenge
derived_from_challenge
adapted_from_challenge
influence_claim_challenge
independent_invention_claim
common_structure_claim
lineage_strength_challenge
lineage_confidence_challenge

Dispute Registry may record whether a lineage relation was:

reaffirmed
corrected
superseded
revoked
deferred
partially_accepted
rejected
Lineage and Governance Bridge

Governance Bridge should ask:

Is the lineage relation explicit or inferred?
Is the relation type appropriate?
Is the source record verifiable?
Is the structural relation specific?
Is independent invention plausible?
Is the lineage disputed?
Does allocation depend heavily on this lineage?

If the answers are unstable, governance should prevent automatic allocation.

Lineage and Anti-Gaming Rules

Lineage claims can be gamed.

Possible abuse includes:

false origin claims
vague influence claims
retroactive lineage insertion
overclaiming common structure
claiming broad conceptual ownership
using weak lineage to capture allocation
hiding independent invention evidence
trace spam to simulate lineage

Anti-Gaming Rules should apply strongly to lineage claims.

Important rule:

Lineage uncertainty should not become lineage entitlement.

Independent Invention

Independent invention is a major issue in lineage assessment.

Two contributors may create similar structures independently.

Indicators:

no access path
different development history
common field constraints
generic structure
independent timestamped records
no trace overlap

If independent invention is plausible, the model should:

increase structure_ambiguity
increase tolerance_band
reduce lineage_confidence
trigger review if allocation depends on lineage

Independent invention should not automatically erase lineage, but it should increase caution.

Common Structure

Some structures are too common to support strong lineage claims.

Example:

problem → analysis → solution → conclusion

This should not produce strong lineage.

A more distinctive structure may be:

trace evidence
→ contribution range
→ tolerance band
→ overlap rule
→ allocation readiness
→ dispute registry

Lineage Engine should distinguish common structure from distinctive architecture.

Multi-Source Lineage

Some works have multiple lineage sources.

Example:

Work D derives from Work A,
adapts Work B,
and is influenced by Work C.

In such cases, Contribution Tolerance Band Model should avoid forcing a single origin.

Possible handling:

multi-source contribution ranges
pooled allocation
shared influence layer
common culture pool
human review

Multi-source lineage often requires wider bands and careful governance.

Lineage Distance

Lineage distance measures how far a target work is from a source.

Example:

Source → Derivative 1 → Derivative 2 → Target

Higher distance may increase uncertainty.

Effect:

higher lineage_distance → higher temporal_uncertainty
higher lineage_distance → wider tolerance_band

However, high distance does not eliminate contribution.

It means the contribution should be assessed with caution.

Lineage Strength and Contribution Type

Different lineage relations imply different contribution types.

Relation Type	Likely Contribution Type
origin_candidate	origin/question/structure contribution
derived_from	derivative contribution
adapted_from	transformation contribution
influenced_by	indirect influence
translated_from	source + translation contribution
remixed_from	multi-source contribution
implemented_from	design-to-implementation contribution
extended_from	extension contribution
forked_from	repository/project lineage
structurally_similar_to	possible structural evidence
conceptually_related_to	weak conceptual evidence

This mapping should be treated as guidance, not final judgment.

Example: Protocol Lineage

Source:

Trace Protocol defines trace paths.

Target:

Contribution Tolerance Band Model uses trace confidence to adjust contribution ranges.

Possible lineage relation:

adapted_from / extended_from

Interpretation:

Trace Protocol supplies connection evidence.
Contribution Tolerance Band Model extends that evidence into uncertainty-aware allocation guidance.

This lineage may support structural relationship, but not ownership by itself.

Example: Lineage to Allocation

Lineage Engine output:

{
  "relation_type": "adapted_from",
  "lineage_strength": "moderate",
  "lineage_confidence": 0.72
}

Contribution Tolerance Band output:

Contributor A: 35% - 50%
Contributor B: 30% - 45%

Allocation Readiness:

pooled_ready

Royalty OS handling:

pooled_allocation

This shows lineage becoming contribution range, not direct allocation.

Example: Disputed Lineage

Lineage Engine output:

{
  "relation_type": "structurally_similar_to",
  "lineage_strength": "weak",
  "lineage_confidence": 0.42,
  "independent_invention_possible": true,
  "disputed": true
}

Contribution Tolerance Band handling:

wider tolerance_band
review_required
possible common_culture_pool

Royalty OS handling:

no automatic allocation
Minimal Integration Pattern
Lineage Engine record
+ Trace Protocol record
+ KSD / Structure Fingerprint
+ Provenance record
+ Signed Impact Attestation
+ Dispute record
        ↓
Contribution Tolerance Band assessment
        ↓
Contribution range
        ↓
Allocation Readiness
        ↓
Governance Bridge
        ↓
Royalty OS policy
What Lineage Engine Should Not Do

Lineage Engine should not:

determine legal ownership
assign royalty shares by itself
treat influence as automatic entitlement
treat structural similarity as proof
ignore independent invention
ignore common structures
overwrite audit history
bypass Dispute Registry
bypass Allocation Readiness
replace human review in high-risk cases

Lineage Engine identifies possible relationships.

Contribution Tolerance Band Model assesses those relationships under uncertainty.

Governance Benefits

Integrating Lineage Engine provides:

clearer relationship classification
better handling of indirect influence
better separation between trace and contribution
stronger evidence structure
better dispute routing
safer allocation decisions
better support for multi-source contribution
more auditable lineage history
Non-Goals

This document does not define the full Lineage Engine specification.

It does not define legal authorship.

It does not enforce payment.

It does not replace Trace Protocol, KSD, or Royalty OS.

It only explains how lineage records should integrate with Contribution Tolerance Band Model.

Design Philosophy

Lineage is not a straight line.

It is often a branching river.

Some streams are visible.
Some flow underground.
Some merge.
Some split.
Some disappear into culture.

Contribution Tolerance Band Model should not force every river into a single pipe.

It should recognize lineage, measure uncertainty, and route the case through appropriate governance.

Summary

Lineage Engine Integration connects lineage classification to contribution assessment.

The core rule is:

Lineage is evidence of relationship, not automatic proof of contribution share.

Lineage Engine identifies possible relationship types.

Contribution Tolerance Band Model converts lineage evidence into uncertainty-aware contribution ranges.

Allocation Readiness decides whether those ranges are stable enough to use.

Dispute Registry handles contested lineage.

Royalty OS applies allocation policy.

This keeps the system flexible, auditable, and resistant to false precision.
