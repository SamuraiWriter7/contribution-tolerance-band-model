# Anti-Gaming Rules

## Status

Draft v0.1  
Related repository: Contribution Tolerance Band Model  
Related architecture: Kazene Royalty OS / Communication Royalty OS  
Related concepts: Band Width Function, Model Weighting, Temporal Adjustment, Allocation Readiness, Review Status, Governance Bridge, Dispute Registry, Trace Protocol, KSD, Structure Fingerprint

---

## One-Line Summary

Anti-Gaming Rules define how Contribution Tolerance Band Model should resist manipulation, artificial uncertainty, false contribution claims, trace spam, and strategic dispute behavior.

The core rule is:

> Uncertainty should not become entitlement.

---

## Why Anti-Gaming Rules Matter

Contribution Tolerance Band Model intentionally allows uncertainty.

It treats contribution as a range:

```text
Contribution Range = estimated_value ± tolerance_band

This is necessary because real contribution is often uncertain.

However, any system that accepts uncertainty can be abused.

Bad actors may try to:

create artificial ambiguity
inflate contribution ranges
flood the system with weak traces
overclaim structural influence
manipulate estimator outputs
submit bad-faith disputes
use vague similarity as entitlement
exploit wide tolerance bands
retroactively insert attribution claims

Anti-Gaming Rules exist to prevent this.

Core Principle

A wider tolerance band means more uncertainty.

It does not mean a stronger claim.

Example:

Contributor A: 10% - 90%

This does not mean Contributor A should receive a large allocation.

It means the system lacks enough certainty.

Recommended handling:

review_required
deferred_allocation
common_culture_pool
disputed_pool
no automatic allocation
Key Rule
Wider uncertainty ≠ wider entitlement

A broad band should reduce allocation readiness.

It should not increase allocation power.

This is one of the most important safety rules in the Contribution Tolerance Band Model.

Gaming Risks

This document addresses the following risks:

artificial_ambiguity
range_inflation
trace_spam
false_provenance
structure_overclaim
similarity_overclaim
model_weighting_manipulation
bad_faith_disputes
retroactive_claim_insertion
evidence_flooding
community_review_manipulation
temporal_gaming
Artificial Ambiguity

Artificial ambiguity occurs when a contributor intentionally makes a claim vague enough to overlap with many works.

Example:

I influenced this general structure because it resembles my earlier idea.

Risk:

vague claim
→ wide band
→ attempted allocation claim

Required response:

increase structure_ambiguity
increase dispute_risk
lower allocation_readiness
require stronger evidence

Artificial ambiguity should not create allocation rights.

Range Inflation

Range inflation occurs when a contributor tries to expand their contribution band beyond what evidence supports.

Example:

Claimed range: 10% - 90%
Evidence-supported range: 35% - 45%

Required response:

flag overclaim risk
compare claim against evidence-supported band
require explanation
trigger review if material

If the claimed range greatly exceeds the evidence-supported range, the claim should be treated as unstable.

Overclaim Risk

Overclaim risk measures whether a contribution claim exceeds the supported evidence.

Possible indicators:

claimed contribution exceeds estimator consensus
claim relies on vague structural similarity
claim lacks trace support
claim ignores counter-evidence
claim expands after value increases
claim appears only after allocation becomes likely

Possible handling:

increase dispute_risk
widen tolerance_band
reduce allocation_readiness
route to human_review or Dispute Registry
Trace Spam

Trace spam occurs when many weak or irrelevant trace records are submitted to create the appearance of influence.

Examples:

excessive self-citation
irrelevant backlinks
repeated low-quality references
circular trace chains
automated attribution links
mass-generated trace records

Risk:

quantity of traces appears high
quality of traces remains low

Required response:

weight trace_quality over trace_quantity
detect circular references
reduce weight of low-quality traces
increase manipulation_risk
trigger review

Trace density alone should not determine contribution.

Trace Quality Rule

A small number of high-quality traces may be stronger than many weak traces.

High-quality trace:

timestamped
verifiable
specific
relevant
non-circular
supported by provenance

Low-quality trace:

vague
self-generated
irrelevant
duplicative
circular
unverifiable

Core rule:

Trace quality matters more than trace quantity.

False Provenance

False provenance occurs when origin records, timestamps, or authorship records are manipulated.

Examples:

fake publication dates
edited repository history
forged attestations
fabricated metadata
manipulated screenshots
retroactive license records
unverifiable archive claims

Required response:

increase manipulation_risk
require provenance verification
lower evidence_strength
trigger review_required
possible Dispute Registry routing

False provenance should block automatic allocation.

Structure Overclaim

Structure overclaim occurs when a contributor claims ownership over a broad or common structure.

Example:

problem → analysis → solution → conclusion

This structure is too generic to support strong contribution claims.

Required response:

increase structure_ambiguity
reduce structural_evidence_strength
consider common_structure_risk
avoid automatic allocation

Only distinctive, specific, trace-supported structures should meaningfully support contribution claims.

Common Structure Rule

Not every structure is attributable.

Some structures are common, generic, or naturally implied by the problem.

Common structures should usually produce:

wider tolerance_band
lower confidence
shared_influence_layer
common_culture_pool
review_required if high-value

A structure must be specific enough to support a contribution claim.

Similarity Overclaim

Similarity overclaim occurs when surface similarity is treated as proof of contribution.

Examples:

similar wording
similar topic
similar tone
similar layout
similar genre convention
similar problem framing

Similarity may be evidence.

But similarity alone is not proof.

Required response:

require trace support
require structure analysis
require provenance support if allocation is involved
avoid high allocation from similarity alone

Core rule:

Similarity is a signal, not a verdict.

Model Weighting Manipulation

Model weighting manipulation occurs when one estimator is over-weighted to force a desired outcome.

Examples:

similarity estimator dominates the result
friendly human reviewer receives excessive weight
provenance evidence is ignored
KSD evidence is treated as final judgment
dispute-aware estimator is removed during a dispute

Required response:

require explicit weights
require weights_sum = 1.0
require weighting rationale
flag unusual weight profiles
allow weighting challenges

Model weighting must be transparent enough to be reviewed.

Estimator Capture

Estimator capture occurs when a contributor or group controls the estimator environment.

Examples:

coordinated community review
biased reviewer pool
model prompts tuned toward one claimant
selective evidence submission
excluding contrary estimators
hiding estimator disagreement

Required response:

increase estimator_variance
lower estimator_agreement
require independent review
route to Governance Bridge

No estimator should become an unquestioned authority.

Bad-Faith Disputes

Bad-faith disputes are challenges submitted to delay, harass, or manipulate allocation.

Examples:

repeated unsupported objections
retaliatory disputes
strategic timing before allocation
vague claims without evidence
mass disputes against competitors
disputes designed to force settlement

Required response:

require evidence
track dispute history
rate-limit repeated weak disputes
flag bad-faith patterns
allow no_action outcome

The right to challenge must be protected.

But the system must also protect contributors from endless bad-faith contestation.

Strategic Dispute Timing

Strategic dispute timing occurs when a party waits until allocation becomes valuable before raising a weak claim.

Indicators:

claim appears after value increases
claimant had prior opportunity to object
evidence is weak or unchanged
dispute targets allocation timing

Required response:

record timing
require stronger evidence
increase dispute_risk
consider provisional allocation
route only disputed portion to disputed_pool

A dispute should not automatically freeze all allocation.

Retroactive Claim Insertion

Retroactive claim insertion occurs when a contributor attempts to insert origin claims after the fact.

Examples:

backdated posts
edited documentation
late-added repository notes
unverifiable “I said this earlier” claims
retroactive attribution metadata

Required response:

require timestamp verification
compare against archived records
check audit history
increase manipulation_risk
do not accept as direct evidence without verification

Retroactive claims may be considered, but only with strong verification.

Evidence Flooding

Evidence flooding occurs when many weak evidence items are submitted to overwhelm review.

Examples:

large numbers of low-relevance links
repeated screenshots
duplicate citations
AI-generated support documents
irrelevant references
noisy similarity reports

Required response:

deduplicate evidence
score evidence quality
ignore irrelevant evidence
summarize evidence bundles
require strongest supporting records

More evidence does not always mean stronger evidence.

Community Review Manipulation

Community review manipulation occurs when public or community feedback is coordinated to influence assessment.

Examples:

vote brigading
popularity pressure
coordinated endorsement
reputation-based pressure
social media amplification
group-based attribution campaigns

Required response:

limit community_review weight
separate popularity from evidence
require trace/provenance support
detect coordination patterns

Community recognition may be useful, but it should not replace evidence.

Temporal Gaming

Temporal gaming exploits time-based rules.

Examples:

waiting for records to disappear
exploiting link rot
claiming stale evidence is invalid
reopening settled cases repeatedly
asserting cultural diffusion to erase origin
using old vague claims to capture new value

Required response:

preserve audit trails
use archived records
track reopening attempts
require new evidence for reopening
do not automatically decay stable evidence

Time should not be used to erase valid contribution.

Cultural Diffusion Abuse

Cultural diffusion can be real.

But it can also be abused.

Example abuse:

This structure is now common, so the originator should receive nothing.

Or the opposite:

This structure became common, so the originator should receive everything.

Both extremes are unsafe.

Required response:

recognize origin where evidence supports it
recognize diffusion where individual attribution weakens
use shared_influence_layer
use common_culture_pool when appropriate
avoid all-or-nothing attribution
Independent Invention Abuse

Independent invention claims may be valid.

But they may also be used to deny real lineage.

Required response:

evaluate trace evidence
evaluate structural specificity
evaluate timing
evaluate access possibility
evaluate field conventions
allow review
avoid automatic dismissal of either side

Independent invention should widen uncertainty unless strongly proven.

Manipulation Risk Score

A future schema version may include:

{
  "manipulation_risk": {
    "score": 0.72,
    "risk_factors": [
      "trace_spam",
      "retroactive_claim_insertion",
      "evidence_flooding"
    ],
    "recommended_action": "human_review"
  }
}

For v0.1, manipulation risk can be reflected through:

dispute_risk
review_required
review_reasons
evidence_strength
estimator_agreement
trace_confidence
notes
Suggested Risk Levels
0.00 - 0.20 → low manipulation risk
0.20 - 0.40 → moderate manipulation risk
0.40 - 0.70 → high manipulation risk
0.70 - 1.00 → severe manipulation risk

Suggested handling:

Risk Level	Suggested Handling
low	Continue normal assessment
moderate	Increase review sensitivity
high	Require human review
severe	Block automatic allocation and route to governance
Review Reasons Related to Gaming

Gaming-related review may use existing review reasons:

high_dispute_risk
counter_evidence_present
manual_review_requested
low_trace_confidence
low_evidence_strength
high_estimator_variance
range_overlap_conflict
other

If other is used, notes should explain the gaming concern.

Example:

review_reasons = ["other"]
notes = "Potential trace spam detected. Several trace records appear circular or low relevance."
Anti-Gaming and Band Width Function

Gaming risk should usually widen the tolerance band or trigger review.

Examples:

trace_spam detected
→ trace_uncertainty increases
→ manipulation_risk increases
→ tolerance_band widens
false provenance suspected
→ evidence_strength decreases
→ dispute_risk increases
→ review_required

However, widening the band should not increase entitlement.

The widened band signals instability.

Anti-Gaming and Model Weighting

Gaming risk should affect estimator weights.

Examples:

similarity overclaim detected
→ reduce similarity_estimator weight

trace spam detected
→ reduce trace_quantity influence
→ increase trace_quality requirement

bad-faith dispute suspected
→ increase dispute-aware review
→ do not automatically freeze all allocation

Weights should adapt to manipulation risk.

Anti-Gaming and Temporal Adjustment

Gaming risk may change over time.

Examples:

retroactive claim appears
→ require timestamp verification

repeated reopening attempts
→ flag bad-faith pattern

records disappear
→ check archived sources before reducing confidence

settled dispute refiled without new evidence
→ possible no_action

Temporal adjustment should distinguish genuine new evidence from strategic timing.

Anti-Gaming and Allocation Readiness

Gaming risk should reduce allocation readiness.

Example:

manipulation_risk = high
→ allocation_readiness = review_required or not_ready

A case should not be allocation-ready if gaming risk is unresolved.

Anti-Gaming and Dispute Registry

Dispute Registry should record both valid disputes and abuse patterns.

It may record:

bad_faith_dispute_pattern
unsupported_repeated_claim
trace_manipulation_claim
false_provenance_claim
strategic_dispute_timing

This helps governance distinguish real challenges from manipulation.

Anti-Gaming and Governance Bridge

Governance Bridge should enforce anti-gaming rules.

It should ask:

Is the uncertainty natural or artificial?
Is evidence strong or merely numerous?
Are trace paths meaningful or spammed?
Are weights transparent?
Is a dispute legitimate or strategic?
Is the claim timely?
Is the structure specific enough?

If the answer is unclear, the case should not proceed automatically.

Anti-Gaming and Common Culture Pool

Common Culture Pool can prevent unsupported individual claims.

Use when:

influence may be real
but origin is unclear
and individual allocation would be unsafe

This prevents both:

false individual capture

and:

complete erasure of diffuse contribution
Anti-Gaming and Disputed Pool

Disputed Pool can prevent premature allocation during unresolved conflict.

Use when:

claim has some support
but counter-evidence or dispute prevents final allocation

Disputed Pool should not be used forever without review.

It should have governance rules for review, release, or reallocation.

Provisional Allocation Under Gaming Risk

Some cases may allow provisional allocation.

Example:

80% stable allocation released
20% held in disputed_pool

Use when:

only part of the claim is disputed
stable evidence supports most allocation
blocking all allocation would be unfair
audit correction is possible

This prevents bad-faith disputes from freezing everything.

Minimal Anti-Gaming Decision Table
Risk	Signal	Recommended Response
Artificial ambiguity	Very wide unsupported band	Review or defer
Trace spam	Many weak traces	Reduce trace weight
False provenance	unverifiable records	Block automatic allocation
Structure overclaim	Generic structure	Use common culture pool or review
Similarity overclaim	Surface resemblance only	Require trace/provenance support
Bad-faith dispute	Repeated unsupported challenge	Record, filter, possible no_action
Retroactive claim	late origin assertion	Require timestamp verification
Evidence flooding	excessive weak evidence	Deduplicate and quality-score
Weight manipulation	unusual estimator dominance	Require weighting review
Temporal gaming	strategic reopening	Require new evidence
Suggested Future Schema Extension

A future schema version may include:

{
  "anti_gaming": {
    "manipulation_risk_score": 0.64,
    "risk_factors": [
      "trace_spam",
      "structure_overclaim"
    ],
    "anti_gaming_actions": [
      "human_review",
      "reduce_trace_quantity_weight",
      "require_provenance_verification"
    ],
    "automatic_allocation_blocked": true,
    "notes": "Trace evidence appears numerous but low-quality and partially circular."
  }
}

For v0.1, these signals can be represented through existing fields and review notes.

Suggested Future Fields

Possible future fields:

anti_gaming.manipulation_risk_score
anti_gaming.risk_factors
anti_gaming.anti_gaming_actions
anti_gaming.automatic_allocation_blocked
anti_gaming.evidence_quality_score
anti_gaming.trace_spam_score
anti_gaming.retroactive_claim_risk
anti_gaming.bad_faith_dispute_risk
anti_gaming.notes
What Anti-Gaming Rules Should Not Do

Anti-Gaming Rules should not:

block all uncertain claims
punish legitimate indirect influence
reject all disputes
assume every late claim is false
assume every structural claim is overclaim
replace human review
replace Dispute Registry
erase valid contribution
freeze allocation forever

The goal is not suspicion.

The goal is resilient governance.

Design Philosophy

A system that accepts uncertainty must also defend against manufactured uncertainty.

A system that accepts traces must defend against trace spam.

A system that accepts structural influence must defend against structure overclaim.

A system that accepts disputes must defend against bad-faith disputes.

Anti-Gaming Rules are not meant to make the system rigid.

They are meant to keep the system flexible without becoming exploitable.

Summary

Anti-Gaming Rules protect Contribution Tolerance Band Model from manipulation.

The central rule is:

Uncertainty should be visible, but it should not be exploitable.

Good anti-gaming design makes the system:

more trustworthy
more allocation-safe
more dispute-resistant
more resistant to trace spam
more resistant to false precision
more resistant to artificial ambiguity
more compatible with Royalty OS governance

Contribution Tolerance Band Model needs flexibility.

Anti-Gaming Rules ensure that flexibility does not become a loophole.
