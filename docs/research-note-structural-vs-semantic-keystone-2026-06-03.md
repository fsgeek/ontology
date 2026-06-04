# Research Note: The Structural/Semantic Keystone — Where the Architecture Earns Its Novelty (and Where It Cannot)

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** June 3, 2026
**Status:** Research note — identifies and sharpens the load-bearing claim of the layered-ontology strawman; falsifiable on the FNMA substrate. Eyes-on-substrate required to settle.
**Origin:** An architectural pressure-test of the layered-ontology strawman, run after the prior-art baseline was verified (`positioning-correction-2026-06-03.md`). Three conceptual seams were worked; two collapse into the third. This note records the keystone seam and the concession it forces, because the concession — counter-intuitively — is what makes the architecture's novelty *defensible* against the verified closest prior art (OKB, arXiv:2605.23297).

---

## 1. The Headline Promise, Stated Precisely

The strawman's distinctive claim (§2): violations live in the *gaps between layers* and are detectable as **structural schema violations at cross-layer boundaries**, "rather than as semantic content the auditor must notice by reading." This is the property that is supposed to do work the flat-list ontologies cannot.

The keystone question: **is that promise true?** Not rhetorically — *structurally*, in the sense that a SHACL engine (or equivalent) can decide the violation without invoking a domain predicate.

## 2. Two Kinds of Gap — and Only One Is Structural

The cross-layer gaps split cleanly into two cases that the strawman currently runs together.

**(a) Presence gaps — genuinely structural.**
A `haber` category with *zero* linked `ser` bindings. A `ser` binding with *zero* linked `estar` evidence nodes. These are pure **cardinality constraints** — `sh:minCount 1` on the cross-layer property. No domain predicate. No reading. A SHACL engine decides them. This case is real and clean.

**(b) Adequacy gaps — NOT structural.**
The gap that actually *matters* for audit is not "no evidence node exists." It is "**no *adequate* / *relevant* evidence exists**." Whether a given `estar` observation *counts as* evidence for a given `ser` commitment is a **relevance / warrant judgment**. SHACL can verify that the edge `evidences(estar_node, ser_binding)` is *present*; it **cannot** verify that the edge is *warranted*. Warrant is semantic content.

## 3. Why This Is the Keystone

Three facts converge on case (b):

1. **OKB already delivers case (a).** The verified closest prior art (Sharma & Kunkel, arXiv:2605.23297) compiles obligations into SHACL over PROV-O evidence graphs. Missing-edge cardinality gaps are exactly what that machinery produces. So **case (a) is not the novelty** — it is table stakes that OKB already meets.

2. **The novelty claim therefore leans on case (b).** The strawman's differentiation must come from the gap that matters — adequacy — because the gap that is structural (presence) is already occupied.

3. **Case (b) is exactly where semantics re-enters.** The `mandatory_features` case makes this vivid and unavoidable. Whether "FICO used in 12% of depth-≤3 trees on conforming cells" *counts as* evidence for / against "the band collectively considers FICO" requires the **band-level predicate** — and the band-level predicate **is** the semantic content. It is, precisely, the pre-registered canonical inference. The warrant of the `evidences` edge is the smuggle point.

So the keystone is the single place where (i) the headline claim is made, (ii) semantics smuggles in, and (iii) the differentiation from OKB is decided. If the note claims SHACL gets adequacy "for free," it **overclaims**, and the differentiation from OKB collapses into "OKB plus hand-curated semantic predicates relabeled as structure."

## 4. The Two Other Seams Collapse Into This One

- **Conflict-preservation (Seam 2)** is only non-trivial if it **changes the generated SHACL shapes** — i.e. if a preserved TILA-vs-UDAP conflict deterministically emits a *different* (richer or differently-shaped) `estar` obligation set than any single collapsed binding does, computable from the conflict graph alone. If preservation does not change the shapes, it is "OKB with extra unused nodes." So Seam 2 does its work *at the cross-layer boundary* — i.e. inside Seam 3 — or not at all. (Its sharper falsifiable form: the `estar` test set under preserved-conflict is a strict superset of, or provably distinct from, the set under every individual collapsed binding; and any resolution event is forced to leave a structural trace as a first-class, provenance-bearing `ser` node. Falsified if collapse-then-test yields the identical test set.)

- **Evidentials-on-the-wrong-layer (Seam 1)** is a clean, contained fix (resolved separately in `resolution-note-constative-performative-2026-06-03.md`): move evidential class off `ser` onto `estar` and onto reports-about-bindings. It bruises the Quechua companion's §5 but does not threaten the core architecture. It is *not* the keystone.

## 5. The Concession — and Why It Strengthens the Claim

The honest move is **not** to defend "adequacy is structural." It is to **concede that adequacy is semantic** and re-scope the contribution accordingly. The granularity case strongly implies the concession is forced.

After the concession, the genuinely-novel residue over OKB is **exactly three things and no more**:

1. **The `haber` scope level** — band vs per-member — which OKB does not model. (This is the original `mandatory_features` diagnosis: the constraint at per-member granularity *cannot bind by construction*.)
2. **Conflict-preservation that changes the generated shapes** (Seam 2, only if it does real boundary work).
3. **Pre-registered, executable adequacy predicates** as the semantic oracle — the canonical inferences, declared in advance and machine-evaluable.

The contribution is therefore **not** "we made adequacy structural" (false). It is "**we made the semantic adequacy predicate pre-registered and executable**" — declared as semantic, not disguised as structural. This is a smaller claim than the headline, and it is *defensible*, where the headline is not. A defensible smaller claim beats an indefensible larger one; that is the whole pre-registration ethos applied to the architecture's own self-description.

## 6. Falsifiable Form (on the FNMA substrate)

The keystone yields a **dissolution test**, not just an assertion:

> **Structural-extension test.** Take each adequacy gap the architecture wants to surface on the FNMA substrate (e.g. "the band's `mandatory_features=FICO` commitment is unsupported"). Attempt to reduce it to a **domain-predicate-free SHACL shape**.
> - If *any* adequacy gap so reduces, the structural claim **extends** there — record it; the structural territory is larger than this note expects.
> - If it **cannot** (the expected case — because adequacy requires the band-level relevance predicate), the architecture **must own** that adequacy is semantic, and that its contribution is making the predicate pre-registered and executable, *not* structural.

And the **presence/adequacy partition** is itself falsifiable:

> All **presence** gaps (missing `haber→ser` and `ser→estar` edges) are expressible as pure SHACL cardinality shapes with **zero domain predicates** — verifiable by exhibiting the shapes. All **adequacy** gaps are carried explicitly by the pre-registered canonical inferences (executable predicates over the substrate). **Falsified if** a presence gap turns out to need a domain predicate (the partition leaks downward), or an adequacy gap turns out to be pure cardinality (the partition leaks upward and the structural territory grows).

## 7. Consequence for Every Downstream Claim

If the concession is forced (as the granularity case implies), then **every downstream novelty claim must be re-scoped to it**:

- The related-work section positions against OKB as "OKB delivers structural presence-gap detection; our contribution is the `haber` scope level OKB lacks, shape-changing conflict-preservation, and pre-registered executable adequacy predicates" — **not** "we make gaps structural where OKB makes them semantic" (false; OKB's gaps are already structural for the presence case).
- The pre-registration's value is precisely that **OKB has no equivalent pre-registered band-level result.** The differentiation is cashed out empirically in the preservation/falsification numbers (see `pre-registration` skeleton work), not asserted architecturally.
- The Rashomon-invariants extension (iteration 2) inherits the same discipline: invariants are *candidate* adequacy predicates, and must survive Jain et al.'s allocation-multiplicity critique (arXiv:2503.16621) before they can stand as institutional commitments.

---

## Appendix: Status and What Settles It

This note is an *argument*, not a result. What settles it is the FNMA substrate:

- The structural-extension test (§6) is run by *attempting* the domain-predicate-free SHACL reduction on real adequacy gaps and seeing whether it succeeds. Eyes-on-substrate.
- The presence/adequacy partition (§6) is settled by exhibiting the actual SHACL shapes and checking whether any leaks across the boundary.
- Until then, the claim of this note is: **the architecture's defensible novelty over OKB is the three residues, and the headline "gaps are structural not semantic" is true only for presence gaps.** If the substrate shows adequacy gaps reducing to pure structure, this note is wrong in the most interesting possible way — and that, too, is research output.

*Companion notes: `resolution-note-constative-performative-2026-06-03.md` (Seam 1), `positioning-correction-2026-06-03.md` (verified baseline). Foundation: `research-note-layered-ontology-strawman-2026-05-13.md`.*
