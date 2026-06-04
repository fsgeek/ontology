# Positioning Correction: Verified Literature Map → Reframed Novelty Claim

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** June 3, 2026
**Status:** Verification result + positioning correction — citations resolved against the live web 2026-06-03; load-bearing for the eventual related-work section
**Origin:** The literature map (`literature-map-perplexity-2026-06-03.md`) was raw, unverified Perplexity output with an explicit fabrication warning. This note records a verification sweep of its load-bearing targets and the positioning corrections that follow. **Verification method:** parallel independent resolution of each target against arXiv API, IETF datatracker REST API, PubMed Central, W3C, OMG/EDM Council, and dblp — real URLs and IDs confirmed, control URLs used to rule out blanket-200 proxies. Six of seven targets are REAL; exactly one is FABRICATED. Specifics of confirmed papers' *internals* (e.g. OKB's 5-tuple) were NOT verified verbatim against PDFs and are flagged provisional.

---

## 1. Verification Result (one line per target)

| Target | Verdict | Resolved identifier |
|---|---|---|
| OKB framework (Sharma & Kunkel) | **REAL** | arXiv:2605.23297, pub. 2026-05-22 |
| Ontological Compliance Gateway (OCG) | **FABRICATED** | no such named artifact exists |
| IETF WCA / WAL-0…3 draft | **REAL (no IETF standing)** | draft-bondar-wca-00, individual submission |
| BEWA (Bayesian Epistemology w/ Weighted Authority) | **REAL (single-author preprint)** | arXiv:2506.16015 (Craig Wright) |
| Jain et al. allocation multiplicity | **REAL** | arXiv:2503.16621, FAccT 2025 |
| Audit-as-code (PMC) | **REAL** | DOI 10.3389/frai.2026.1759211, PMC12979488 |
| FIBO / FinRegOnt / PROV-O / OBO scope | **REAL (all four)** | edmcouncil/fibo; finregont.com; w3.org/TR/prov-o; OBO FP-005 |

**Net:** 6 real, 1 fabricated. The fabrication is **not** the one the literature map flagged as highest-risk. The map worried OKB was a convergent fabrication; in fact OKB is real, and the fabrication is OCG — which the map had listed as a *lower*-priority target.

## 2. The Three Corrections That Matter

### 2.1 Strike OCG. Replace with the real, crowded cluster it gestures at.

The "Ontological Compliance Gateway (OCG)" framework does not exist. No arXiv paper, no product, no standards artifact uses the name. **It must not be cited as prior art, competitor, or baseline.**

But the strawman must *not* over-claim novelty in the vacuum. The concept OCG gestured at — a neuro-symbolic layer keeping agentic systems within governance bounds by bridging normative and operative — is **densely occupied by real 2026 work**:
- **GRACE** (arXiv:2601.10520): reason-based neuro-symbolic containment that explicitly *decouples* normative reasoning from operative decision-making (the closest real match to "bridging normative and operative").
- **Foundation AgenticOS / "Ontology-Constrained Neural Reasoning in Enterprise Agentic Systems"** (arXiv:2604.00555): ontologies constrain agent I/O including compliance checking.
- **G-SPEC** (arXiv:2512.20275): neuro-symbolic policy enforcement with a Governance Triad + SHACL.

Lesson: here the fabrication was *not* a novelty signal. The program's usual heuristic ("Perplexity fabrication = novelty signal") **inverts for OCG** — the phantom names a crowded space, not an empty one. Worth recording as a counter-example to the heuristic.

### 2.2 OKB is the baseline to BEAT — and it is NOT independent convergence.

OKB (arXiv:2605.23297, Sharma & Kunkel) resolves exactly as cited and is the closest extant SHACL+PROV-O compliance-block instantiation. **But the literature map's conclusion calls it "independently converged upon," and that is false.** OKB continues the *same authors'* COMPSAC 2025 "ontological blocks of meaning" line — one research lineage, not independent parties arriving separately.

**Correction:** reframe from *"the field is independently converging on our architecture"* (a comforting but false novelty-by-corroboration story) to *"OKB is the closest extant instantiation and the mandatory related-work comparison we must differentiate against."* The honest novelty residue over OKB is exactly three things (see §3 and the companion keystone note):
1. the **haber scope-level** (band vs per-member) — OKB does not model this;
2. **conflict-preservation that changes the generated SHACL shapes** — only novel if it does real work at the cross-layer boundary;
3. **pre-registered, executable adequacy predicates** as the semantic oracle.

The *haber/ser/estar* framing itself is novel as a named decomposition (no prior art uses the labeling), but the underlying existence/normative/operative separation maps onto deontic logic and OKB — so the novelty is in the framing and the three residues, not in the separation per se.

> **Provisional caveat:** OKB's *internals* (the claimed 5-tuple, PROV-O links, "deterministic regulatory compiler") were confirmed only at the metadata level, not read verbatim from the PDF. Before the related-work section is drafted, read the OKB PDF and confirm the 5-tuple specifics. Cite specifics provisionally until then.

### 2.3 Two real citations are double-edged — engage, do not lean on.

- **Jain et al., "Allocation Multiplicity"** (arXiv:2503.16621, FAccT 2025; full authors Jain, Wang, Creel, Wilson). This is the **most dangerous** real citation. It argues equally-good models need not yield an equally-good *allocation* space — failures from sampling limits, deterministic selection, and structural bias. This directly undercuts **Rashomon-invariants-as-commitments**: a Rashomon-invariant may not map to an institutional commitment. **Cite as a threat the design is built to expose, never as corroboration.** It is part of why iteration 1 is correctly hand-curated, and the pre-registration's scope-leak falsification condition is built to surface (not paper over) the multiplicity problem.
- **WCA draft** (draft-bondar-wca-00) and **BEWA** (arXiv:2506.16015): both real, both **single-author, non-peer-reviewed, no institutional standing** (WCA is an individual IETF submission explicitly "not endorsed by the IETF"; BEWA is a Craig Wright preprint). Cite **for existence only, with provenance disclosed, NEVER as independent corroboration** of the attestation / belief-ledger framing. Since Willay attestation is explicitly deferred (strawman §5), neither should be load-bearing in iteration 1. Additional note: BEWA is explicitly *truth-promoting*, which is closer to truth-attestation than to the strawman's deliberately truth-agnostic belief-attestation stance — so it does not even support the framing it was cited for.

## 3. What Survived Clean

- All four conventional anchors (FIBO, FinRegOnt, PROV-O, OBO scope FP-005) verify and are correctly characterized. Cosmetic refinements only: FIBO "supports/aligns with" BCBS 239 / MiFID II / Dodd-Frank rather than encoding a formal per-regulation mapping; EDM Council owns, OMG publishes; cite OBO Principle 5 as "Scope (FP-005)."
- **Conflict-preservation-not-collapse**: least-contested novelty claim; no prior-art artifact surfaced against it.
- **Pre-registration applied to ontology-architecture testing**: unchallenged; no extant collision. But note **Audit-as-code** (PMC12979488) is real prior art for "policy-as-code / map governance to auditable rules in advance" — frame pre-registration as a *stricter* discipline layered on top, not as the same idea claimed fresh.

---

*This note supersedes the literature map's "independent convergence" framing. The map remains useful as a search map; this note records which of its targets are real and how the verified baseline tightens — not loosens — the strawman's commitments. Tony owns check-in / sign / push.*
