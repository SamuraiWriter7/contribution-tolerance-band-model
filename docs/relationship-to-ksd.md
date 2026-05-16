# Relationship to KSD / Structure Fingerprint

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: KSD, Structure Fingerprint, Structure Lineage, Trace Protocol

---

## One-Line Summary

KSD and Structure Fingerprint provide structural evidence for Contribution Tolerance Band Model.

They help determine whether a contribution exists at the level of structure, question, pattern, transformation, or lineage.

---

## Why This Relationship Matters

Contribution is not always visible as a direct citation.

In many creative, technical, and AI-mediated contexts, contribution may appear as:

- a structural idea
- an original question
- a conceptual pattern
- a protocol architecture
- a transformation rule
- a lineage relation
- a repeated design structure
- an indirect influence

These forms of contribution may not be captured by simple citation tracking.

For example, a later work may not quote an earlier work directly, but it may inherit its structure.

This is where KSD and Structure Fingerprint become important.

They allow Contribution Tolerance Band Model to consider deeper structural evidence.

---

## Basic Relationship

```text
KSD / Structure Fingerprint
        ↓
Structural Evidence
        ↓
Contribution Tolerance Band Model
        ↓
Contribution Range
        ↓
Allocation / Review / Dispute Handling

KSD does not determine final contribution by itself.

Instead, it supplies structural evidence.

Contribution Tolerance Band Model then uses that evidence to adjust the contribution range and tolerance band.

What KSD Provides

KSD may provide machine-readable structural records such as:

origin question
core concept
structural pattern
transformation logic
protocol architecture
semantic skeleton
lineage markers
versioned structure
derivative relation
structural similarity signal

These records help distinguish between superficial similarity and structural inheritance.

What Structure Fingerprint Provides

Structure Fingerprint may provide compact evidence about the structural identity of a work.

It may describe:

recurring conceptual architecture
question-answer structure
procedural flow
relation between components
design grammar
transformation chain
high-level semantic pattern
protocol-level shape

A structure fingerprint is not the same as surface text similarity.

It is intended to capture deeper organization.

Surface Similarity vs Structural Similarity

This distinction is critical.

Surface Similarity

Surface similarity means the text, wording, or expression looks similar.

Example:

Two articles use similar phrases.

This may be useful, but it is not always strong evidence of contribution.

Structural Similarity

Structural similarity means the underlying pattern, question, or architecture is similar.

Example:

Two protocols use the same evidence → trace → allocation → dispute flow.

This may indicate deeper lineage even if the wording is different.

Contribution Tolerance Band Model should treat these as different evidence types.

How KSD Affects the Tolerance Band

KSD evidence can narrow or widen the tolerance band.

Strong KSD Evidence

If KSD shows strong structural continuity, the tolerance band may narrow.

Example:

High structural continuity
+ clear origin question
+ matching transformation pattern
+ supporting trace record
= smaller tolerance band

Example output:

Contributor A: 42% - 50%
Weak KSD Evidence

If KSD shows only vague similarity, the tolerance band should remain wide.

Example:

General thematic similarity
+ no clear origin question
+ no trace path
+ no timestamped record
= wider tolerance band

Example output:

Contributor A: 20% - 65%

This should likely trigger review rather than automatic allocation.

KSD Is Evidence, Not Final Judgment

KSD should not be treated as a final authority.

It is evidence.

A strong KSD record may increase confidence.

A weak KSD record may increase uncertainty.

A disputed KSD record may trigger review.

But KSD alone should not automatically determine ownership, royalty share, or final contribution.

This model follows the principle:

Structure can support contribution claims, but structure alone should not become automatic entitlement.

Contribution Types Supported by KSD

KSD can help identify several types of contribution.

origin_question_contribution
structural_design_contribution
conceptual_architecture_contribution
transformation_pattern_contribution
protocol_lineage_contribution
semantic_framework_contribution
derivative_structure_contribution

These types are especially important when direct citations are incomplete or absent.

Example: Origin Question Contribution

A contributor may provide the original question that later structures an entire system.

Example:

Original question:
How can contribution be measured without false precision?

Later system:
Contribution Tolerance Band Model

Even if the later system has different wording, the original question may be structurally important.

KSD can preserve this relation.

Contribution Tolerance Band Model can then treat it as structural evidence.

Example: Protocol Architecture Contribution

A contributor may design a protocol architecture.

Example:

Permission
→ Trace
→ Evidence
→ Contribution Range
→ Allocation
→ Dispute Handling

If later systems reproduce this architecture, KSD may indicate structural lineage.

Contribution Tolerance Band Model may then assign a contribution range based on the strength of that structural evidence.

Example: Transformation Pattern Contribution

A contributor may create a transformation pattern.

Example:

fixed contribution score
        ↓
interval-based contribution range
        ↓
tolerance-band allocation

If this transformation pattern appears in later works, KSD can identify it.

The model can then assess whether the pattern is specific enough to count as contribution evidence.

Evidence Strength Levels

KSD-based evidence may be classified into levels.

high_structural_evidence
moderate_structural_evidence
weak_structural_evidence
unclear_structural_evidence
disputed_structural_evidence
High Structural Evidence

Use when:

the structural pattern is specific
the origin record is timestamped
the lineage path is clear
the transformation pattern is preserved
supporting trace evidence exists

Effect:

tolerance_band narrows
confidence increases
review risk decreases
Moderate Structural Evidence

Use when:

structural similarity is meaningful
some lineage signals exist
trace evidence is partial
direct evidence is incomplete

Effect:

tolerance_band remains moderate
human review may be useful
Weak Structural Evidence

Use when:

similarity is broad or thematic
no specific pattern is preserved
trace evidence is missing
multiple possible origins exist

Effect:

tolerance_band widens
automatic allocation should be avoided
Disputed Structural Evidence

Use when:

another contributor challenges the lineage
counter-evidence exists
estimator outputs disagree
provenance records conflict

Effect:

review_required = true
possible Dispute Registry routing
Suggested JSON Mapping

KSD-related records may appear in the relationships section:

{
  "relationships": {
    "ksd_record_ids": [
      "ksd-record-001"
    ],
    "structure_fingerprint_ids": [
      "sf-record-001"
    ]
  }
}

They may also appear in the evidence bundle:

{
  "evidence": {
    "structural_evidence": [
      {
        "evidence_id": "ev-structure-A-001",
        "evidence_type": "structure_fingerprint",
        "source_id": "ksd-record-001",
        "description": "Structure fingerprint indicates strong similarity between the origin specification and the assessed target work.",
        "strength": 0.82,
        "confidence": 0.80
      }
    ]
  }
}
Relationship to Evidence Strength

KSD evidence affects evidence_strength.

Example:

{
  "evidence_strength": 0.78
}

If KSD evidence is strong and supported by trace or provenance records, evidence strength may increase.

If KSD evidence is weak, broad, or unsupported, evidence strength should remain limited.

Relationship to Structure Ambiguity

KSD evidence affects structure_ambiguity.

Example:

{
  "uncertainty_factors": {
    "structure_ambiguity": 0.18
  }
}

A lower structure_ambiguity value means the structural relation is clearer.

A higher value means the structural relation is uncertain.

clear KSD lineage → lower structure_ambiguity
vague similarity → higher structure_ambiguity
Relationship to Tolerance Band

KSD evidence directly affects the tolerance band.

Example:

Strong KSD evidence:
estimated_value = 0.46
tolerance_band = 0.04
range = 0.42 - 0.50

Example:

Weak KSD evidence:
estimated_value = 0.46
tolerance_band = 0.20
range = 0.26 - 0.66

The second case is too uncertain for safe automatic allocation.

Relationship to Estimator Agreement

Multiple estimators may interpret KSD evidence differently.

For example:

Structure Estimator: strong lineage
Provenance Estimator: weak direct proof
Trace Estimator: partial trace path
Human Reviewer: moderate confidence

If these estimators agree, the tolerance band may narrow.

If they diverge, the tolerance band should widen.

KSD therefore works best when combined with Multi-Estimator Consensus.

KSD and Multi-Estimator Consensus

KSD should not stand alone.

It should be interpreted alongside:

provenance evidence
trace evidence
citation evidence
signed attestations
human review
dispute records
estimator consensus

This prevents structural similarity from becoming overclaim.

The system should avoid this failure mode:

similar structure = automatic contribution claim

Instead, it should use this safer logic:

similar structure
+ trace support
+ provenance support
+ estimator agreement
= stronger contribution range
KSD and Yin-Yang Balance

KSD often belongs to the Yin side of contribution evidence.

It captures hidden, structural, indirect, or long-term influence.

Yin Influence:
- origin question
- structural similarity
- conceptual lineage
- transformation pattern
- implicit influence

Direct evidence belongs more to the Yang side.

Yang Evidence:
- citation
- timestamp
- signature
- repository history
- publication record

Contribution Tolerance Band Model needs both.

Too much Yang creates a system where only explicit records matter.

Too much Yin creates a system where vague influence claims dominate.

KSD helps reveal hidden structure, but it must be balanced with visible evidence.

Review Triggers Related to KSD

A case should trigger review when:

KSD evidence is strong but direct evidence is weak
KSD evidence conflicts with provenance evidence
multiple KSD records claim different origins
structure similarity is high but trace path is missing
structure ambiguity exceeds threshold
counter-evidence challenges structural lineage
economic allocation is high-value

These cases should not move directly to automatic allocation.

They should move to review, pooled allocation, deferred allocation, or Dispute Registry.

Example Flow
1. A target work is submitted for contribution assessment.

2. KSD extracts or references its structural pattern.

3. Structure Fingerprint compares the target work to prior records.

4. The system detects possible structural lineage.

5. Contribution Tolerance Band Model treats this as structural evidence.

6. The model combines it with trace, provenance, attestation, and review evidence.

7. A contribution range is produced.

8. If the range is narrow and evidence is strong, allocation may proceed.

9. If the range is wide, overlapping, or disputed, review is triggered.
What KSD Should Not Do

KSD should not:

claim legal ownership
replace copyright analysis
prove absolute originality
automatically assign royalty shares
treat all structural similarity as contribution
ignore independent invention
ignore common patterns or public-domain structures
override dispute handling

KSD is a structural evidence layer, not a final allocation engine.

Independent Invention

A major risk in structural analysis is mistaking independent invention for lineage.

Two contributors may arrive at similar structures independently.

This is especially common when:

the problem naturally leads to similar solutions
the structure is simple or generic
the field has shared conventions
multiple people respond to the same external event
the structure is part of common knowledge

In such cases, KSD evidence should widen the tolerance band rather than force attribution.

Possible handling:

independent_invention_possible = true
review_required = true
allocation_recommendation = deferred_allocation or common_culture_pool
Common Structure vs Original Structure

Not every structure is uniquely attributable.

Some structures are common.

Example:

problem → analysis → solution → conclusion

This is too generic to support strong contribution claims.

Other structures may be more specific.

Example:

trace evidence
→ contribution range
→ tolerance band
→ overlap rule
→ allocation readiness
→ dispute registry

This may be more structurally distinctive.

KSD should help distinguish between common structure and original structure.

Governance Benefits

By integrating KSD with Contribution Tolerance Band Model, the system gains:

deeper recognition of structural contribution
better handling of indirect influence
reduced dependence on surface text similarity
stronger trace-based attribution
clearer uncertainty modeling
safer allocation decisions
better dispute routing
lower risk of false precision
Minimal Integration Pattern
KSD record
+ Structure Fingerprint
+ Trace Protocol record
+ Provenance record
+ Signed Impact Attestation
        ↓
Contribution Tolerance Band assessment
        ↓
Contribution range
        ↓
Allocation recommendation

This keeps KSD modular.

KSD supplies structural evidence.

Contribution Tolerance Band Model transforms that evidence into an uncertainty-aware contribution range.

Royalty OS decides how allocation should proceed.

Non-Goals

This document does not define the full KSD specification.

It does not define the full Structure Fingerprint specification.

It does not determine legal authorship.

It does not claim that structural similarity automatically proves influence.

It only explains how KSD and Structure Fingerprint can serve as structural evidence for Contribution Tolerance Band Model.

Summary

KSD and Structure Fingerprint are essential because contribution is not always visible on the surface.

They help detect:

question-level contribution
structure-level contribution
protocol-level contribution
lineage-level contribution
transformation-level contribution

Contribution Tolerance Band Model uses these signals to adjust the contribution range.

The core rule is:

KSD can strengthen a contribution claim, but it should not automatically finalize one.

Structure is evidence.

Trace is connection.

Tolerance Band is judgment under uncertainty.

Together, they allow contribution to be assessed without false precision.
