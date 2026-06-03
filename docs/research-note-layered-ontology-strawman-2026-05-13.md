# Layered Ontology for ML Governance — Strawman Proposal

**Author:** Tony Mason / wamason.com LLC
**Date:** May 13, 2026
**Status:** Strawman / Pre-pre-registration draft — not for distribution
**Origin:** Synthesis emerging from a May 13, 2026 conversation exploring ontology design for ML governance, building on the schema findings from the Olorin work, the epistemic honesty impossibility paper, the Hamut'ay autobiographer/biographer distinction, and the Willay attestation architecture. Documented separately because the ontology line of work warrants independent development from the governance-codification work currently flowing to the public Olorin repository.

---

## 1. Problem Statement

Current ontologies for ML governance — including FIBO, internal-policy YAML schemas, and the flat-feature-list patterns used in production governance code — fail in a specific way. They encode constraints at the wrong granularity, provide no structural mechanism for the institution to attest to what it has committed versus what is empirically operative, and collapse the distinction between *the act of fixing a term's meaning* and *the term itself*. The failure mode is silent misrepresentation: the schema validates, the data passes, the audit produces a clean report, and yet the substrate is doing something materially different from what the ontology says it is doing. This is the structural property that makes hiding in a 10-Q so easy.

The Olorin schema work on FNMA stratified data produced a concrete instance. `mandatory_features` encoded as a flat per-member list presupposes that "feature consideration" is a binary per-member-per-feature property — each individual model either uses feature *f* or does not. On real data, this presupposition fails universally: depth-≤3 trees on FM cells use 1–5 features each, and the institutional commitment the constraint is trying to encode is at the *band* level — the band of admissible models considers these features collectively, as an institutional commitment, not each individual model. The constraint as written cannot bind; it operates at the wrong granularity by construction. (Reference: case #11 in the Olorin schema findings, 2026-05-13.)

This is not a defect of `mandatory_features` specifically. It is a symptom of the underlying ontology being unable to *represent the granularity at which institutional commitments live*. The same failure mode recurs for any term whose institutional meaning is at a different scope than its naive encoding suggests.

## 2. Architecture Claim

A three-layer ontology architecture, structured on the Spanish grammatical distinction between *haber*, *ser*, and *estar*, surfaces granularity mismatches and analogous failures as structural schema violations at cross-layer boundaries.

**Haber layer — existence declaration.** The ontology declares that a category exists at a specific scope. "There is a category `mandatory_features` that applies at the *band* level." The scope is part of the declaration; without it, the category is incompletely specified.

**Ser layer — institutional definition commitment.** The ontology encodes the institutional commitment about what the term essentially means, with provenance for the binding moment: which authority, when, under what regulatory or policy construction. Each binding event is a first-class object, not a property of the term. Binding moments accumulate; conflicts between them are surfaced rather than collapsed. ("Consumer" under TILA is bound differently than "consumer" under state UDAP statutes; the ontology shows both.)

**Estar layer — operative binding evidence.** The ontology records what the substrate is empirically doing — which models in this deployment, under this jurisdiction, are actually instantiating this term's commitment. The estar layer is evidence-bearing, not declarative. It is populated from the experimental harness and the deployed system's observed behavior, not from policy documents.

Each layer fails differently. *Haber failure:* the category doesn't exist or is scoped wrong (the `mandatory_features` case). *Ser failure:* institutional commitment is missing, conflicted, or unattested. *Estar failure:* operative behavior diverges from declared commitment — the 10-Q hiding case.

Critically, schema violations live in the *gaps between layers* at least as much as within them. A category that exists in haber but has no ser attestation is an undefined commitment. A ser commitment with no estar evidence is unverified institutional speech. An estar observation that does not match its ser commitment is the central audit failure mode. The architecture's claim to do work the current flat-list ontologies cannot do rests on its ability to make these cross-layer gaps visible as structural properties rather than as semantic content the auditor must notice by reading.

## 3. Pre-Registered Prediction (Strawman)

For the `mandatory_features` case on Olorin's FNMA substrate:

A set of *N* hand-curated canonical inferences about `mandatory_features` will be specified before the test suite runs. Each inference takes the form: "Given `mandatory_features = [f_1, f_2, ...]` for this band, the following property must hold of any admissible model's behavior on FM cells of [specified type]." Example form: "If `mandatory_features` lists FICO at the band level, the band must collectively use FICO in ≥*X*% of depth-≤3 trees on conforming-loan FM cells."

The prediction commits, in advance:

- *N* (the count of canonical inferences)
- The specific inferences (text-stated, formally expressible as executable predicates)
- The fraction of FNMA cells expected to fail under the per-member flat-list encoding
- The fraction of FNMA cells expected to preserve under the band-level encoding
- The diagnostic signature of "preservation failure" — what counts, structurally, as a license-preservation breach

The architecture claim is falsified if the band-level encoding does not preserve substantially better than the per-member encoding on the same suite. It is also falsified if the canonical inferences preserve identically under both encodings (which would mean the architectural distinction has no operative consequence on the substrate as it exists).

The concrete numbers — specific *N*, specific inferences, specific fractions, specific cells — must be written down before any test code runs. This is the pre-registration discipline carried over from the governance work; it is what distinguishes the strawman from architectural advocacy.

## 4. Minimum Viable Scope

- One term: `mandatory_features`
- One jurisdiction: US federal mortgage (FNMA substrate)
- One model class: depth-≤3 trees on FM cells
- One binding moment: the relevant FHFA construction, or an internal-policy stand-in if no clean external binding exists
- One license-preservation suite (initially hand-curated; see Open Design Questions)

The scope is deliberately tight. The strawman's job is to falsify (or fail to falsify) the smallest version of the architecture claim. Larger scope before the smallest claim is settled repeats the failure mode the strawman is supposed to detect: premature feature accretion at the wrong granularity.

## 5. Explicitly Deferred to Later Iterations

- FIBO integration (build-on vs. replace; almost certainly build-on, but the integration is a separate workstream)
- Willay attestation chain for binding moments (the ser-layer attestation infrastructure)
- Cross-jurisdictional translation (Scotiabank-shape multi-regime cases)
- Frame semantics (Fillmore-style) for rung-4 terms whose frames are not shared by receiver
- Quechua-evidential attestation types (-mi / -si / -chá) as a richer epistemic marking system
- Stateful hash-based signatures (XMSS/LMS) for long-duration premium-tier attestations
- Tiered service offering (cheap routine attestation vs. premium institutional commitment)

Each is part of the architectural picture and warrants its own treatment. None can be productively designed until the smallest claim is testable. The discipline of deferral is itself part of the methodology.

## 6. Open Design Questions

### 6.1 Hand-curated vs. empirically-derived canonical inferences

Hand-curated: we select inferences we believe should preserve based on regulatory and policy reasoning. Empirically derived: we identify inferences that are invariant across a Rashomon set of equally-accurate models on the same substrate. The two approaches should converge if the ontology is well-formed; where they diverge is itself a research finding.

**Initial recommendation:** hand-curated for the first iteration, with empirically-derived added as a planned extension. Hand-curated is smaller, more interpretable, and produces more diagnosable failure modes. Empirical derivation extends the test surface significantly and integrates naturally with the Rashomon-routed-decision methodology already in the research program — the Rashomon set provides the empirical analogue of canonical inferences, and convergence between hand-curated and Rashomon-derived sets is a strong signal that the architecture is tracking something real about the substrate's institutional structure.

### 6.2 Inference formalization

Canonical inferences need to be expressible in a form the test suite can evaluate. Natural-language statement plus an executable predicate is the minimum; richer logical encoding (Datalog, OWL-DL, SHACL) is possible but probably premature. The right move for the first iteration is the simplest expressible form that admits machine evaluation against the FNMA substrate.

### 6.3 Diagnostic granularity

When an inference fails preservation, what level of detail does the test suite surface? "FICO not used in 12% of conforming cells" is one level. "FICO not used in 12% of conforming cells, specifically in cell strata *X*, *Y*, *Z*, with structural correlations to feature *Z*'s coverage" is another. The richer signal is more useful as research output but harder to specify in advance, and the specification itself becomes a falsifiable claim about what the architecture should be able to surface.

### 6.4 Authority for the binding moment

In the production case, the binding authority for `mandatory_features` would be FHFA, the GSE itself, the institution's compliance function, or some composition. For the strawman, an internal-policy stand-in is sufficient and probably preferable — the point is to test the architecture, not to enact actual regulatory binding. But the stand-in should be explicit, not implicit, so that the eventual move to a real binding authority is a substitution rather than a redesign.

## 7. Connection to Adjacent Work

This strawman is one of several lines in a broader research program on declared-incompleteness systems — systems that know what they cannot represent and surface those gaps rather than concealing them.

- **Hamut'ay** (autobiographer/biographer cliff): the same structural property applied to memory systems. An ontology that declares its own losses behaves differently than one that does not, and the difference is externally visible. The strawman applies that property to governance ontology.
- **Willay** (cryptographic attestation): the substrate that makes binding moments first-class with non-repudiation. Eventually carries the ser-layer attestation chain. Deferred from this iteration to keep the smallest claim isolable, but the architecture is designed to accept Willay as the ser-layer substrate when it is ready.
- **Yanantin** (graph memory substrate): the natural storage for layered ontology with binding-moment provenance and cross-frame translation edges. The relationships between bindings, terms, and operative evidence are graph-shaped by construction.
- **Olorin governance work** (schema findings): the empirical anchor. Case #11 (`mandatory_features` at wrong granularity) is the smallest concrete failure of flat-list ontology that this work explains. The strawman uses the governance work's data as its substrate without requiring the governance work itself to flow into this line.
- **Rashomon-routed-decision methodology**: the source of empirically-derived canonical inferences in the second iteration. Inferences invariant across the Rashomon set of equally-accurate models on the substrate are candidates for band-level institutional commitment, and convergence with hand-curated inferences is a cross-validation of both.
- **Epistemic honesty impossibility paper**: the philosophical grounding for belief-attestation (rather than truth-attestation) as the tractable form. The ontology stores what the institution committed to believing at a time, not what the institution claims is true.

## 8. Methodological Notes

This work uses the pre-registered prediction discipline carried over from prior governance work. Concrete numbers — *N*, fractions, cells, diagnostic signatures — must be committed in writing before the test suite runs. The discipline is what distinguishes the strawman from architectural advocacy and what allows the manifold to be felt around rather than circled.

The strawman is intentionally lightweight in form. The artifact is this note plus a runnable license-preservation suite; the suite is what falsifies. If the architecture survives the `mandatory_features` test, the next iteration extends to a second term (likely "consumer" under a specified policy construction) and begins integrating Willay attestation. If the architecture fails, the failure mode is itself research output and shapes the next architectural iteration.

The audience for this strawman is the research program itself — self-falsification, not external review. The framing and scope here would shift substantially for a regulator-facing version or a Olorin-facing version, and those are explicitly future artifacts, not this one.

## 9. Next Steps

1. Write the concrete pre-registered prediction (specific *N*, specific inferences, specific fractions, specific cells) before any test code runs. This step requires eyes-on-substrate; the Claude-code instance currently working with the FNMA data is the natural collaborator.
2. Build the minimal license-preservation suite around the pre-registered prediction.
3. Run on Olorin's actual FNMA data.
4. Report findings whichever way they go.
5. Decide on second iteration (additional term, Rashomon-derived inferences, Willay attestation integration) based on what the first iteration reveals.

---

*This note is the foundation document for the layered ontology line of work. It is deliberately incomplete in places where completion would be premature. The incompleteness is part of the methodology.*
