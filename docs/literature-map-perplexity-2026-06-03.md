# Literature Map (Perplexity) — Layered Ontology for ML Governance

> **EPISTEMIC STATUS — READ BEFORE USING.**
> This document is raw output from **Perplexity**, run by Tony Mason on
> 2026-06-03 against `research-note-layered-ontology-strawman-2026-05-13.md`.
> **The citations are UNVERIFIED.** Perplexity has a known fabrication failure
> mode for specific references; this research program explicitly tracks it (see
> Arbiter memory `feedback_citation_verification.md`: "Citations are a model weak
> spot; Tony verifies independently; Perplexity fabrication = novelty signal").
> The prompt was kept neutral, which lowers but does not eliminate the risk.
>
> Treat this as a **search map** (where to look), NOT a **reference list**
> (what is there). Do not cite anything below until the specific reference has
> been independently resolved. Treat every 2025–2026 arXiv ID, author+venue+year,
> and "closest prior art" claim as a hypothesis to check, not a fact.
>
> **Highest-priority verification targets** (most load-bearing if real, most
> suspicious if convergent-and-fabricated):
> - "OKB framework (Sharma & Kunkel, arXiv:2605.23297, May 2026)" — claimed as
>   *"the closest extant instantiation of the strawman's architecture."* If real,
>   it is the primary prior-art comparison and reshapes the novelty claim. If
>   fabricated, that is itself a novelty signal.
> - "Ontological Compliance Gateway (OCG) framework (2026)"
> - "IETF WCA (Warrant Certificate Authority) draft, WAL-0…WAL-3"
> - "Epistemic Ledger" / "BEWA (Bayesian Epistemology with Weighted Authority)"
> - "Dai et al., FAccT 2025"; "Langlade et al. 2025"; "Jain et al. allocation
>   multiplicity"; "deontic KG for IoT-Reg, arXiv:2601.03587"; "Audit-as-Code (PMC 2026)".
>
> **Likely-solid (conventional, verifiable, correctly characterized at the
> category level):** FIBO (OMG/EDM Council), PROV-O, SHACL, OWL-DL, deontic logic,
> LKIF, Open World Assumption, OBO Foundry scope principle. The *categories* of
> prior art are probably right even where specific recent papers are not.
>
> **Most useful part regardless of citation-truth:** §9 (the novelty table) and
> §10 (adjacencies) — they map where to look. The headline novelty judgments
> (haber/ser/estar decomposition "not found"; Rashomon-*invariants*-as-commitments
> a novel application; conflict-*preservation*-not-collapse a novel design
> decision) are verifiable by search and are the claims that matter for positioning.
>
> **Status:** preserved marked, NOT yet verified. Verification pass deferred until
> the ontology paper's related-work section is being drafted (the moment the
> citations become load-bearing). Tony owns check-in / sign / push of this file.

---

# Literature Map: Layered Ontology for ML Governance

## Overview

The strawman proposes a three-layer ontology architecture (using the Spanish copula distinction *haber/ser/estar*) for ML governance, aimed at surfacing commitment–evidence gaps that flat-list ontologies like FIBO silently conceal. This report maps each substantive claim in the strawman to relevant prior literature, identifies where the ideas are well-explored, where they are partially explored, and where the specific synthesis appears genuinely novel.

***

## 1. The Central Diagnostic: Silent Misrepresentation in Compliance Ontologies

The strawman's core diagnosis — that existing compliance ontologies encode constraints at the wrong granularity, causing schema validation to pass while the substrate does something materially different — is well-recognized in the ontology engineering literature but has rarely been operationalized as a structural design requirement.

The problem of **scope mismatch** (also called granularity mismatch) in ontologies is documented in the ontology alignment and combination literature. Combining or reusing ontologies introduces mismatches in the part of the domain covered and the level of detail, which can create silent semantic incompatibilities without surface-level validation failures. The OBO Foundry principles explicitly require that each ontology term carry a clearly stated scope and that out-of-scope terms be placed in separate importable modules — a principle directly addressing the kind of per-member vs. band-level confusion the strawman identifies.[1][2][3]

The specific failure mode — a schema that validates while the operative system contradicts the declared constraint — is described in the compliance ontology literature as the distinction between **declarative** and **operative** governance. Current documentation-centric compliance relies on prose obligations and static checklists; the audit produces a clean report because it checks the declarative layer, not the operative substrate. The strawman names this the "10-Q hiding case." This framing is novel in its specificity to ML model governance, though the underlying problem (declared policy diverging from operative behavior) is a recognized failure mode in data governance more broadly.[4][5][6][7]

***

## 2. Layered Ontology Architecture

### 2.1 Layered / Multi-Level Ontologies in General

Layered ontology as a structural idea — multiple dependent, non-reductively related layers, each with its own operational primitives — has substantial prior literature. The philosophical treatment by Nakamura et al. (PhilArchive) describes a world-as-VM metaphor where each layer has distinct truth conditions and interfaces, and traditional ontologies operate as "layer-specific virtual machines". This is structurally isomorphic to the strawman's architecture but is applied to world-description philosophy rather than ML governance engineering.[8]

The Gasser/Almeida layered governance model for AI (Social/Ethical, Legal/Regulatory, Technical) is the most widely cited three-layer governance framework in AI policy. It explicitly treats layers as interdependent rather than hierarchical, with changes in one rippling through others — echoing the strawman's cross-layer gap logic. However, it does not provide a *formal* mechanism for detecting inter-layer mismatches; it is descriptive rather than structurally enforceable.[9]

Anthropic's governance stack (Constitution → RSP → System Card) is a documented real-world instance of a layered policy architecture where each layer serves a different purpose: normative, risk-evaluative, and empirical. The observation that boundaries are "not fixed" at any layer, and that the evaluation layer cannot "confidently rule out" compliance thresholds, is precisely the gap the strawman seeks to make structural rather than semantic.[10]

### 2.2 The Haber/Ser/Estar Distinction as Ontological Architecture

The specific use of the Spanish copula triad (*haber* = existence declaration, *ser* = essential/institutional commitment, *estar* = empirical/operative state) as an organizing principle for a compliance ontology is **not found in the existing literature**. The linguistic distinction is well-established in Spanish grammatical theory, and ontologists have used natural-language copula structures to motivate ontological distinctions (notably the Basic Formal Ontology's distinction between continuants and occurrents), but the *haber/ser/estar* triad specifically — applied to the problem of separating existence-scope, institutional-definition, and operative-evidence layers in a governance ontology — appears to be an original framing.[11]

The closest formal analog in the existing literature is the **deontic logic** tradition, which distinguishes between what *is* the case, what *ought* to be the case, and what *is permitted/obligatory* to be the case. Deontic compliance ontologies (including LKIF, IoT-Reg, and various GDPR compliance ontologies) explicitly separate normative obligations from operative facts and provide inference machinery for detecting gaps between them. The strawman's *ser* layer maps closely to the "obligation" layer in deontic frameworks; the *estar* layer maps to the "operative fact" layer. The *haber* layer (existence declaration with scope) is less commonly made explicit in deontic ontologies — it is usually implicit in the ontology's class hierarchy — which is arguably where the strawman adds the most formal novelty.[12][13][14]

***

## 3. Binding Moments as First-Class Objects

The strawman treats each term's institutional definition-commitment as a **binding event** (a first-class object with provenance: authority, timestamp, regulatory construction) rather than a static property of the term. Conflicting bindings accumulate and are surfaced rather than collapsed.

This idea is directly anticipated by **PROV-O** (the W3C Provenance Ontology), which provides classes and properties for representing provenance information, including who generated an artifact, when, and under what activity. PROV-O is designed to record the derivation and attribution history of data, making it a natural substrate for the *ser*-layer's binding-event record. Several compliance ontology systems (including the OKB framework and GDPR provenance work) already use PROV-O to link compliance assertions to their regulatory source.[6][15][16][17]

The idea that **multiple conflicting bindings should coexist** rather than resolve into a single authoritative definition is less commonly implemented. Ontology alignment literature notes the problem of conflicting definitions across jurisdictions and standards (e.g., "consumer" under TILA vs. state UDAP) but typically treats this as an integration challenge to be resolved rather than a design feature to be preserved. The strawman's insistence that conflicts be *surfaced* rather than *collapsed* is a meaningful design decision with roots in the Open World Assumption (OWA) of OWL, where absence of a statement is not treated as falsity. However, the OWA's handling of conflicts is generally passive (underdetermination) rather than active (structured accumulation with explicit conflict marking), so the strawman's approach is a more assertive variant.[18][19][20][1]

The **deontic binding** literature (covering imposed, voluntary, and autogenic binding of normative powers) provides formal vocabulary for the *ser* layer's authority-and-scope structure, though it has not been applied to ML governance ontologies in the specific way the strawman describes.[21]

***

## 4. Cross-Layer Gaps as Structural Schema Violations

The strawman's most operationally distinctive claim is that violations should live in the *gaps between layers* — detectable as structural schema violations at cross-layer boundaries, not as semantic content that an auditor must notice by reading.

This structural approach to compliance gap detection is the central contribution of the **Ontological Knowledge Blocks (OKB)** framework (Sharma & Kunkel, arXiv:2605.23297, May 2026). OKBs formalize compliance as a 5-tuple binding normative obligations to an RDF/OWL concept schema, executable SHACL validation rules, explicit evidence requirements, and PROV-O provenance links. The deterministic regulatory compiler translates regulatory obligations into machine-checkable constraints over structured evidence graphs, enabling violations to appear as SHACL constraint failures rather than as semantic gaps requiring human interpretation. This is the closest extant instantiation of the strawman's architecture, though it does not use the *haber/ser/estar* decomposition and does not specifically address the granularity-mismatch failure mode.[7][6]

**SHACL** (Shapes Constraint Language) and **OWL-DL** are the standard substrate for expressing cross-layer constraints in ontology-based compliance systems. The ontology-based compliance audit framework literature (for GDPR, NIS2, and similar regulations) consistently uses a combination of deontic logic for obligation representation and SHACL/SWRL for operative constraint checking. The gap the strawman is targeting — no structural mechanism to detect that a *ser*-level commitment lacks *estar*-level evidence — is a known limitation of these systems, which tend to check whether declared obligations are met but do not systematically check whether declarations are themselves grounded in operative evidence.[22][23][24]

The **Ontological Compliance Gateway (OCG)** framework (2026) explicitly addresses the problem of ensuring agentic AI systems remain within governance bounds, using a neuro-symbolic architecture to bridge normative layers and operative behavior. This is architecturally close but focused on real-time behavioral containment rather than institutional commitment auditing.[25]

***

## 5. Rashomon Set as Source of Empirically-Derived Canonical Inferences

The strawman proposes using the Rashomon set of equally-accurate models on a substrate as a source of *empirically-derived* canonical inferences — properties invariant across all equally-good models constitute candidates for institutional commitment at the band level.

The **model multiplicity / Rashomon set** literature is active and well-developed. The standard application is fairness: among all equally-accurate models, which achieve fairness properties, and how intentional must selection be? The 2025 FAccT work by Dai et al. provides theoretical results on Rashomon set size, the probability of prediction flips, and the distribution of fairness metrics within the set. The 2025 work on Fairness and Sparsity within Rashomon sets (Langlade et al.) introduces enumeration-free mathematical programming methods for characterizing properties within the Rashomon set, applicable to any hypothesis class.[26][27][28][29][30]

The strawman's specific use — extracting *invariant properties* across the Rashomon set as candidate institutional commitments — has not been used in this way in the published literature. Existing work extracts *variable* properties (fairness, sparsity, robustness) to show that model selection matters, but does not use *invariant* properties as a cross-validation target for hand-curated governance commitments. This is a genuine application novelty. The 2025 allocation multiplicity paper (Jain et al.) raises a related concern: equally-good models may not reflect an equally-good allocation space, implying that Rashomon-set invariants may not straightforwardly map to institutional commitments in resource-allocation contexts. This is a known risk worth building into the strawman's validation design.[31][32]

***

## 6. Declared-Incompleteness Systems and Epistemic Attestation

The broader research program frames the layered ontology as one instance of a "declared-incompleteness system" — a system that knows what it cannot represent and surfaces gaps rather than concealing them. The governance framing uses belief-attestation (what the institution committed to believing) rather than truth-attestation.

**Epistemic attestation** as a formal concept is well-developed in the AI epistemic integrity literature. The Epistemic Ledger framework formalizes belief states as cryptographically anchored, append-only records of epistemic events, with each committed belief assigned a justification object encoding provenance as a directed acyclic graph. This directly anticipates the *ser*-layer's binding-moment records. The Bayesian Epistemology with Weighted Authority (BEWA) framework similarly operationalizes belief as a probabilistically coherent function over structured claims, with cryptographic anchoring and zero-knowledge audit verification. Both are more general than the specific governance-ontology application, but confirm that the epistemic-belief-rather-than-truth framing is being formalized elsewhere.[33][34]

The IETF WCA (Warrant Certificate Authority) draft addresses a structurally similar problem at the data-source level: data crossing tool-call boundaries acquires interface trustworthiness rather than the institutional standing of its actual source (termed "semantic laundering"). The graduated Warrant Attestation Levels (WAL-0 through WAL-3) are analogous to the strawman's tiered attestation vision, applied to LLM agent tool calls rather than governance ontologies.[35]

The **open/closed world assumption** literature is directly relevant to the declared-incompleteness architecture. OWL's Open World Assumption means that absent information does not imply falsity — the system is structurally declared-incomplete by default. The strawman goes further: it wants the system to *actively mark* what is unknown or unattested (a *haber* entry with no *ser* binding is explicitly flagged as an undefined commitment) rather than simply not asserting it. This "active incompleteness marking" is less common in standard OWL practice but has been explored in the mixed OWA/CWA literature.[19][20][36][37]

***

## 7. FIBO and Financial Regulation Ontologies

FIBO (Financial Industry Business Ontology), the strawman's named point of comparison, is a modular OWL 2 DL ontology covering legal entities, contracts, securities, loans, and derivatives, maintained by the EDM Council and standardized by OMG. FIBO explicitly aims to provide unambiguous shared meaning for financial terms and aligns with BCBS 239, MiFID II, and Dodd-Frank. Its architecture is **flat in the commitment dimension** — it provides canonical definitions of terms but does not record *when* a definition was bound, *by what authority*, or *whether operative systems are actually using the term as defined*. This is precisely the gap the strawman targets.[38][23][39][40]

The **Financial Regulation Ontology (FRO / FinRegOnt)**, which combines FIBO with LKIF (Legal Knowledge Interchange Format), adds regulatory rule encoding on top of FIBO's entity definitions. This brings it closer to the *ser* layer's regulatory-binding provenance, but still lacks operative-evidence binding to actual model behavior. The reasoning challenges in FIBO (documented at CEUR-WS 2023) confirm that real-world FIBO instantiation is difficult, supporting the strawman's preference for a build-on rather than build-from-scratch approach.[41][42]

***

## 8. Pre-Registration Discipline in Ontology and Governance Research

The strawman explicitly adopts pre-registration discipline — committing to specific predictions (N inferences, fractions, cells, diagnostic signatures) before any test code runs — as a methodological guard against architectural advocacy masquerading as empirical finding.

Pre-registration is standard in clinical and social science research but is uncommon in ontology engineering or ML governance research. The closest analog in the ML literature is the formal specification of evaluation criteria in **algorithmic auditing** frameworks (where criteria must be defined before examining model behavior to prevent post-hoc rationalization). The "Audit-as-Code" framework (PMC, 2026) maps governance requirements to technically-auditable rules in advance of execution, which is structurally similar. The pre-registration of canonical inference counts and preservation fractions before running the license-preservation suite is a stricter form of this discipline and has no direct precedent in the ontology-based compliance literature reviewed here.[43]

***

## 9. Where the Strawman is Novel vs. Well-Explored

| Dimension | State in Literature |
|-----------|---------------------|
| Granularity mismatch in compliance ontologies | Well-documented problem; architectural solutions are partial[1][3] |
| Layered governance architecture (3+ layers) | Well-explored at policy level; less formalized[10][9] |
| PROV-O for binding-moment provenance | Standard technique; used in GDPR/compliance work[6][15] |
| SHACL for cross-layer constraint checking | Standard technique in compliance ontologies[23][24] |
| Deontic logic for normative/operative gap | Active research area; IoT-Reg, LKIF, etc.[12][14] |
| OKB framework (normative + SHACL + PROV-O) | Close prior art, May 2026[6][7] |
| Rashomon set for fairness selection | Well-explored[26][27][29] |
| Rashomon invariants as governance commitment candidates | Novel application |
| *Haber/ser/estar* triad as ontology decomposition | Not found in literature |
| Active incompleteness marking (gap = schema violation) | Partial — OWA is passive; active marking less explored[19][37] |
| Binding conflicts preserved, not collapsed | Novel design decision |
| Belief-attestation rather than truth-attestation | Emerging in epistemic integrity literature[33][34] |
| Pre-registration in ontology/governance research | Not found as explicit prior art |

***

## 10. Key Adjacencies Worth Engaging

Several bodies of literature are directly relevant to the next iterations of the strawman:

- **SHACL + PROV-O compliance systems**: The OKB framework (arXiv:2605.23297) is the closest extant system and a natural point of comparison for the license-preservation suite. The strawman's band-level granularity distinction is a concrete extension OKBs do not currently handle.[6]

- **Deontic knowledge graphs for IoT-Reg privacy compliance** (arXiv:2601.03587): Provides an implemented example of a normative layer + operative enforcement layer architecture with provenance and audit, in a domain (disaster management data) that shares the multi-jurisdiction, multi-authority structure of the FNMA substrate.[14]

- **Rashomon set fairness literature (FAccT 2025, arXiv:2501.15634)**: The theoretical machinery for characterizing invariant properties within the Rashomon set is available; applying it to institutional commitment cross-validation is a straightforward but unstated extension.[27][29]

- **Epistemic Ledger / Epistemic Pipelines**: The *ser*-layer's binding-moment records are functionally an epistemic ledger; this literature provides formalization and cryptographic anchoring techniques (including hash-chained sequencing) directly relevant to the Willay attestation integration deferred in the strawman.[44][33]

- **Open/Closed World Assumption mixing** (CEUR-WS Vol. 846): The mixed OWA/CWA design is the formal substrate for "active incompleteness marking" — knowing when to treat an absent binding as an explicit gap vs. an open-world unknown.[37]

***

## Conclusion

The strawman's central ideas — layered governance ontology, commitment–evidence separation, binding-moment provenance, and cross-layer gap visibility as structural schema violations — are well-motivated by the existing literature and are being independently converged upon (the OKB framework is the closest parallel, published May 2026). The specific synthesis is original: the *haber/ser/estar* decomposition, the use of Rashomon-set invariants as empirically-derived canonical inferences for governance commitment validation, the insistence on preserving rather than collapsing conflicting bindings, and the pre-registration discipline applied to ontology architecture testing are not found as a combined package. The strawman is working at the productive edge of an active field, not reinventing established ground.
