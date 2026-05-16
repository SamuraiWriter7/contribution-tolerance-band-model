# Relationship to Trace Protocol

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Trace Protocol, KSD, Structure Fingerprint, Dispute Registry, Royalty OS

---

## One-Line Summary

Trace Protocol provides trace paths.  
Contribution Tolerance Band Model interprets those trace paths as uncertainty-aware contribution ranges.

Trace Protocol answers:

> What is connected?

Contribution Tolerance Band Model answers:

> How strongly should that connection count as contribution under uncertainty?

---

## Why This Relationship Matters

Contribution cannot be assessed without traces.

A contribution claim may depend on:

- access history
- reference history
- citation path
- transformation path
- influence path
- derivative relation
- review history
- provenance record
- structural lineage
- dispute record

Trace Protocol provides the connective tissue between works, contributors, records, and later outputs.

However, a trace alone does not automatically determine contribution.

A trace may be:

- direct
- indirect
- partial
- inferred
- disputed
- incomplete
- weak
- strong
- noisy
- ambiguous

Contribution Tolerance Band Model exists to interpret these traces without pretending that every trace has the same strength.

---

## Basic Relationship

```text
Trace Protocol
      ↓
Trace Evidence
      ↓
Contribution Tolerance Band Model
      ↓
Contribution Range
      ↓
Allocation / Review / Dispute Handling

Trace Protocol provides evidence.

Contribution Tolerance Band Model converts that evidence into an explainable contribution range.

Royalty OS or another allocation system may then use that range to decide how allocation should proceed.

What Trace Protocol Provides

Trace Protocol may provide records such as:

access trace
influence trace
reference trace
transformation trace
audit trace
attribution trace
derivative trace
review trace
dispute trace
provenance trace

These traces help establish relationships between contributors, works, systems, and outputs.

Trace Is Not Allocation

A trace should not be treated as automatic entitlement.

Example:

Work A is connected to Work B.

This does not automatically mean:

Contributor of Work A receives 40% of Work B.

Instead, Contribution Tolerance Band Model asks:

How strong is the trace?
How direct is the connection?
How much structural continuity exists?
How much uncertainty remains?
Is the claim disputed?
Should allocation be automatic, pooled, deferred, or reviewed?

This prevents trace systems from becoming overclaim engines.

Trace Confidence

Trace confidence measures how reliable and meaningful a trace path is.

Example values:

high_trace_confidence
moderate_trace_confidence
low_trace_confidence
unclear_trace_confidence
disputed_trace_confidence

In the JSON model, this may appear as:

{
  "trace_confidence": 0.74
}

Higher trace confidence generally narrows the tolerance band.

Lower trace confidence generally widens the tolerance band.

Trace Strength vs Trace Confidence

This model distinguishes between trace strength and trace confidence.

Trace Strength

Trace strength indicates how significant the connection appears to be.

Example:

The later work strongly depends on the earlier work.
Trace Confidence

Trace confidence indicates how reliable the evidence for that connection is.

Example:

The connection is supported by clear logs, timestamps, and references.

A trace may be strong but uncertain.

A trace may also be weak but well documented.

Contribution Tolerance Band Model should consider both.

Direct Trace

A direct trace is an explicit connection between records.

Examples:

direct citation
explicit reference
linked repository
commit history
access log
signed attestation
license record
quoted source
C2PA-style provenance

Direct traces usually increase confidence and narrow the tolerance band.

Example:

Direct trace present
+ strong timestamp
+ explicit reference
= narrower tolerance band
Indirect Trace

An indirect trace is a connection inferred through structure, context, or transformation.

Examples:

similar protocol structure
inherited conceptual pattern
repeated question structure
design lineage
transformation pattern
semantic architecture
non-explicit influence

Indirect traces may be important, but they usually require wider tolerance bands unless supported by other evidence.

Example:

Indirect trace present
+ structural similarity
+ no explicit reference
= wider tolerance band
Inferred Trace

An inferred trace is a probabilistic or analytical connection.

It may come from:

structure comparison
similarity estimation
lineage inference
multi-estimator analysis
human review
contextual reasoning

Inferred traces should be handled carefully.

They may support contribution assessment, but they should not automatically create strong allocation claims.

A strong inferred trace should still require:

supporting evidence
estimator agreement
review availability
dispute handling
Disputed Trace

A trace is disputed when one or more parties challenge the connection.

Examples:

contributor denies influence
another origin claim exists
trace path conflicts with provenance
timestamps conflict
counter-evidence exists
independent invention is plausible

Disputed traces should widen the tolerance band and may trigger review.

Example:

{
  "trace_confidence": 0.42,
  "dispute_risk": 0.76,
  "review_required": true,
  "review_reasons": [
    "high_dispute_risk",
    "counter_evidence_present"
  ]
}
Missing Trace

A missing trace does not automatically mean no contribution exists.

Some influence may be structural, cultural, or implicit.

However, missing trace evidence should increase uncertainty.

Example:

Strong structural similarity
+ missing trace path
= wider tolerance band
= review or deferred allocation

Contribution Tolerance Band Model allows the system to recognize possible influence without overclaiming certainty.

How Trace Protocol Affects the Tolerance Band

Trace evidence can narrow or widen the tolerance band.

Strong Trace Evidence
clear trace path
+ direct reference
+ timestamped record
+ supporting provenance
= smaller tolerance band

Example:

Contributor A: 42% - 50%
Weak Trace Evidence
partial trace path
+ inferred relation
+ weak provenance
+ no explicit reference
= larger tolerance band

Example:

Contributor A: 25% - 65%

The second case should not proceed to automatic allocation.

Trace Evidence in JSON

Trace records may appear in the relationships section:

{
  "relationships": {
    "trace_protocol_record_ids": [
      "trace-path-001",
      "trace-path-002"
    ]
  }
}

They may also appear inside the evidence bundle:

{
  "evidence": {
    "trace_evidence": [
      {
        "evidence_id": "ev-trace-A-001",
        "evidence_type": "trace_path",
        "source_id": "trace-path-001",
        "description": "Trace path links the contributor's initial structure to the later protocol formulation.",
        "strength": 0.74,
        "confidence": 0.76
      }
    ]
  }
}
Relationship to Evidence Strength

Trace Protocol contributes to evidence_strength.

Example:

{
  "evidence_strength": 0.78,
  "trace_confidence": 0.74
}

If trace records are clear and supported by provenance or direct references, evidence strength may increase.

If trace records are vague, partial, or disputed, evidence strength should remain limited.

Relationship to Trace Uncertainty

Trace Protocol also affects trace_uncertainty.

Example:

{
  "uncertainty_factors": {
    "trace_uncertainty": 0.22
  }
}

A lower trace_uncertainty value means the trace path is clearer.

A higher value means the trace path is less reliable or more ambiguous.

clear trace path → lower trace_uncertainty
missing or disputed trace path → higher trace_uncertainty
Relationship to Estimator Agreement

Different estimators may interpret the same trace differently.

Example:

Trace Estimator: high confidence
Structure Estimator: moderate confidence
Provenance Estimator: low confidence
Human Reviewer: review recommended

When estimators agree, the tolerance band may narrow.

When estimators diverge, the tolerance band should widen.

Trace Protocol is strongest when combined with Multi-Estimator Consensus.

Trace Protocol and Multi-Estimator Consensus

Trace Protocol should not be interpreted by a single estimator alone.

A safer pattern is:

trace evidence
+ structural evidence
+ provenance evidence
+ attestation evidence
+ human or community review
        ↓
multi-estimator consensus
        ↓
contribution tolerance band

This prevents the system from treating a single trace as conclusive proof.

Trace Types and Suggested Effects
Trace Type	Typical Effect
Direct trace	Narrows tolerance band
Provenance trace	Narrows tolerance band
Access trace	Supports connection but may require context
Influence trace	Supports contribution but may remain uncertain
Transformation trace	Supports structural contribution
Audit trace	Improves accountability
Dispute trace	Widens tolerance band or triggers review
Missing trace	Widens tolerance band
Inferred trace	Requires supporting evidence
Trace Protocol and Yin-Yang Balance

Trace Protocol often connects Yang evidence and Yin influence.

Yang Side

Trace records may include visible proof:

timestamp
citation
repository log
publication record
access record
signature
provenance metadata
Yin Side

Trace records may also point to hidden influence:

conceptual lineage
structural resonance
transformation pattern
indirect influence
long-term diffusion

Contribution Tolerance Band Model uses trace evidence to balance these two sides.

Too much reliance on explicit trace may ignore hidden structural contribution.

Too much reliance on inferred trace may create unsupported claims.

The model seeks the middle balance.

Range Overlap and Trace Evidence

Trace evidence can affect whether contribution ranges overlap.

Example:

Contributor A: 42% - 50%
Contributor B: 39% - 47%

If A and B have overlapping ranges, Royalty OS may avoid strict ranking.

Possible handling:

pooled_allocation
equalized_allocation
human_review
shared_influence_pool

Trace Protocol helps explain why the ranges overlap.

Contribution Tolerance Band Model decides how that overlap should affect allocation guidance.

Review Triggers Related to Trace Protocol

A case should trigger review when:

trace path is missing
trace path is disputed
trace confidence is below threshold
trace records conflict
trace suggests influence but structure evidence is weak
structure evidence is strong but trace path is missing
direct trace and inferred trace disagree
high-value allocation depends on trace interpretation
counter-evidence challenges the trace

These cases should not move directly to automatic allocation.

They should move to review, deferred allocation, pooled allocation, or Dispute Registry.

Relationship to Dispute Registry

Trace disputes should be recorded rather than hidden.

If a trace relation is challenged, the case may be routed to Dispute Registry.

Dispute Registry may record:

objection
correction
supersession
revocation
reaffirmation
review outcome

Contribution Tolerance Band Model should use dispute records to adjust:

dispute risk
confidence
tolerance band width
review status
allocation recommendation
Relationship to Allocation Readiness

Trace Protocol is a major input to Allocation Readiness.

Allocation Readiness may ask:

Is this trace-supported contribution assessment ready for allocation?

Contribution Tolerance Band Model helps answer this by providing:

trace confidence
trace uncertainty
evidence strength
estimator agreement
dispute risk
tolerance band width
allocation recommendation

If trace confidence is high and the band is narrow, the case may be allocation-ready.

If trace confidence is low or contested, allocation should be delayed or reviewed.

Example Flow
1. A target work is submitted for contribution assessment.

2. Trace Protocol records relationships between prior works, contributors, and the target work.

3. Trace records are classified as direct, indirect, inferred, disputed, or missing.

4. Contribution Tolerance Band Model uses those traces as evidence.

5. The model combines trace evidence with KSD, Structure Fingerprint, provenance, attestations, and estimator outputs.

6. The model produces contribution ranges.

7. If ranges are narrow and non-conflicting, allocation may proceed.

8. If ranges overlap, widen, or become disputed, the system recommends pooling, review, deferral, or Dispute Registry routing.
Minimal Integration Pattern
Trace Protocol record
+ KSD / Structure Fingerprint
+ Provenance record
+ Signed Impact Attestation
+ Dispute record
        ↓
Contribution Tolerance Band assessment
        ↓
Contribution range
        ↓
Allocation recommendation
        ↓
Royalty OS policy

This keeps the system modular.

Trace Protocol records connections.

Contribution Tolerance Band Model interprets connection strength under uncertainty.

Royalty OS decides allocation behavior.

What Trace Protocol Should Not Do

Trace Protocol should not:

automatically assign royalty shares
determine legal ownership
treat every trace as equal
treat inferred influence as proven contribution
ignore dispute records
ignore missing evidence
replace human review in high-risk cases
collapse uncertainty into false precision

Trace Protocol records relationships.

Contribution Tolerance Band Model evaluates those relationships under uncertainty.

Independent Invention and Trace Gaps

A major risk in trace-based systems is over-attribution.

Two contributors may create similar structures independently.

Trace gaps should therefore be handled carefully.

Example:

Strong structural similarity
+ no trace path
+ plausible independent invention
= wider tolerance band
= review_required

Possible outcomes:

deferred_allocation
common_culture_pool
human_review
dispute_registry

This prevents the system from converting structural similarity into unsupported entitlement.

Trace Density

Trace density describes how many meaningful trace records support a contribution claim.

High trace density may include:

multiple citations
repeated references
repository links
timestamped records
structural matches
signed attestations
review confirmations

High trace density generally narrows the tolerance band.

Low trace density generally widens the band.

However, trace density alone is not enough.

The quality and relevance of traces also matter.

Trace Quality

Trace quality considers:

reliability of the source
clarity of the relationship
timestamp integrity
provenance support
resistance to manipulation
consistency with other evidence
relevance to the assessed contribution

A small number of high-quality traces may be stronger than many weak traces.

Contribution Tolerance Band Model should weigh quality over quantity.

Trace Manipulation Risk

Trace systems may be attacked.

Possible manipulation includes:

artificial self-references
spam citations
fake provenance records
circular references
low-quality trace flooding
coordinated attribution claims
retroactive trace insertion

When manipulation risk is detected, the tolerance band should widen and review should be triggered.

Possible handling:

{
  "review_required": true,
  "review_reasons": [
    "high_dispute_risk",
    "counter_evidence_present",
    "manual_review_requested"
  ]
}
Governance Benefits

By integrating Trace Protocol with Contribution Tolerance Band Model, the system gains:

clearer contribution pathways
better auditability
uncertainty-aware trace interpretation
safer allocation decisions
stronger dispute routing
reduced false precision
better protection against trace manipulation
stronger relationship to KSD and provenance systems
Non-Goals

This document does not define the full Trace Protocol specification.

It does not define legal ownership.

It does not enforce payment.

It does not guarantee that every trace represents contribution.

It does not claim that missing traces eliminate all possible influence.

It only explains how Trace Protocol can provide trace evidence for Contribution Tolerance Band Model.

Summary

Trace Protocol provides the paths.

Contribution Tolerance Band Model provides the uncertainty-aware interpretation.

Royalty OS provides the allocation policy.

The core rule is:

A trace is evidence of connection, not automatic proof of contribution.

Contribution Tolerance Band Model turns trace evidence into contribution ranges, review triggers, and allocation recommendations.

This allows trace-based royalty systems to remain flexible, auditable, and resistant to false precision.
