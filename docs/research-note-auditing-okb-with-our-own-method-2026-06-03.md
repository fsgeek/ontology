# Research Note: Auditing the Closest Prior Art (OKB) With Our Own Method

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** June 3, 2026
**Status:** Research note + correction — code-verified against the OKB repository at clone time; supersedes two overclaims in the 2026-06-03 keystone and positioning notes. Falsifiable; ceiling stated in §6.

> ⚠️ **PARTIALLY REFUTED 2026-06-04.** A line audit of the camera-ready PDF (`/tmp/okb-inspect/paper/main_camera_ready.pdf`) refuted the §4 finding ("the paper under-describes its own code") — the paper *explicitly* describes group-level granularity in four places. The §6 falsification condition triggered. §4 and the "so was OKB's paper" clause in §3.2 are struck below; the four-item **residue** in §5 survives intact (re-verified against newer commit `02a5bdb`). See `research-note-okb-verification-reconciliation-2026-06-04.md` for the full disposition. Do not quote §4 as a live finding.
**Origin:** After the keystone note (`research-note-structural-vs-semantic-keystone-2026-06-03.md`) located the four-item novelty residue over OKB *from the paper*, we applied the project's own discipline — *check the operative substrate, do not trust the declaration* — to OKB's released code (`github.com/AasishKumarSharma/open-knowledge-blocks`). The audit corrected two of our four residue claims, strengthened a third, and surfaced a `ser`/`estar` divergence inside OKB itself. This note records all four, because two of the original claims would have been refuted by any reviewer who opened the repository.

---

## 1. Why Read the Code At All

The verification sweep confirmed OKB's metadata; the full-text fetch confirmed its method *as described*. Both are `ser`-layer evidence: they tell us what OKB's authors *declare* the system does. The project's entire premise is that declarations diverge from operative behavior, and that the divergence is only visible if you inspect the substrate. To position against OKB on the strength of its abstract or even its prose would be to commit, against our nearest rival, exactly the error the architecture is built to catch: taking the `ser` (the paper's claims) as evidence of the `estar` (what the SHACL shapes actually enforce).

So we cloned the repository and read the shapes, the validation engine, and the IR→SHACL compiler. The audit ceiling is stated in §6.

## 2. What OKB's Code Actually Enforces

The fairness block's compiled shapes (`okb_regulatory_compiler_mvp1/generated/shapes_fairness.ttl`, IR at `ir/fairness.yaml`):

- **B1–B4: pure presence.** `sh:minCount 1` on `hasExplanation`, `explanationURI`, `fairnessThreshold`, `allocatedGPUHoursGroupA`. Each checks that a property *exists*.
- **B5: the one value-check.** A SHACL-SPARQL constraint computing `ratio = |a − b| / max(a,b)` and `FILTER(?ratio > ?t)` — where `a = allocatedGPUHoursGroupA`, `b = allocatedGPUHoursGroupB`, `t = fairnessThreshold`.
- **Provenance block** (`blocks/kb_provenance/shapes.ttl`): `prov:wasGeneratedBy` `sh:minCount 1`; generating activity `prov:used` `sh:minCount 2` ("at least a ModelArtifact and a LogArtifact"). Again — pure presence/cardinality.

The validation engine (`okb/validate.py`) is a thin `pyshacl.validate` wrapper; profile composition (`build_shapes_graph`) is **set union of TTL files**. The compiler docstring states the design choice explicitly: *"interpretation is human-responsibility; compilation is deterministic."*

## 3. The Four Residue Claims, Corrected Against Code

### 3.1 Adequacy — STRENGTHENED (we were right; the code makes it sharper)

OKB's only value-check, B5, compares `a`, `b`, `t` that are **all self-declared in the same evidence graph**. Nothing checks that the declared GPU-hours correspond to any operative reality, or that an `Explanation` linked by `hasExplanation` actually explains anything. **OKB validates the declaration against itself; it never reaches operative behavior.** The paper says "adequacy is deferred to application/domain logic"; the code shows the deferral is total. This is, precisely, the `ser`-validated-against-`ser` pattern — the schema passes while the substrate is untouched. The keystone note's claim that OKB delivers *presence* but not *adequacy* holds, and is firmer in code than in prose.

### 3.2 Granularity — CORRECTED (~~and so was OKB's paper~~ — *that second clause struck 2026-06-04; see below*)

> ⚠️ **2026-06-04 correction:** The line audit showed OKB's paper *accurately* describes its group-level granularity ("per-group allocations," Listing 1, "richer multi-group metrics are expressible within the same framework"). ~~and so was OKB's paper~~ is **struck**. The corrected reading: OKB operates at population-group granularity **and says so**; there is no `ser`/`estar` divergence here. The surviving distinction — OKB's group = partition of *subjects* vs. our band = set of *admissible models* — is unaffected and is the part that matters.

The keystone and positioning notes claimed, on the paper's authority, that OKB has "no granularity / group-level / per-obligation only." **This is false in the code.** `allocatedGPUHoursGroupA`/`GroupB`, the IR item `B4` titled *"Decision must declare group allocation totals,"* and `FairnessDisparityShape` are **group-level constraints.** OKB *does* operate at a group granularity.

The residue survives, but only when re-stated precisely:

- OKB's "group" is a **partition of the population** (group A vs group B — a fairness axis over *subjects*).
- Our `mandatory_features` "band" is a **set of admissible models** considering a feature *collectively* (an axis over *models*).

These are different axes. The corrected, reviewer-proof claim is **not** "OKB has no group scope" (refutable by opening the repo) but: **"OKB's collective constraints range over population partitions; it has no constraint that ranges over the set of admissible models (a model-band). The `mandatory_features` band-level commitment has no analog in OKB."**

### 3.3 Conflict — CORRECTED (narrowed twice)

The keystone note framed our novelty as "OKB preserves conflicts, we make preservation generative." Two corrections:

1. (From the paper full text, already noted: OKB's prose says it "preserves conflicts and reports them as validation failures.")
2. **(From the code:) there is no conflict model at all.** Profiles compose by naive set union of shapes. Two conflicting obligations simply become two shapes that may both fail. There is no conflict *concept*, no preservation-as-design, no resolution.

Corrected claim: **"OKB has no representation of conflicting bindings; composition is set union. Our contribution is not 'preservation' (which OKB's prose overstates and its code does not implement) but conflict as a first-class, *generative* object — a preserved conflict deterministically emits a different `estar` obligation set, computable from the conflict graph."** The original "we preserve, they preserve" framing is withdrawn.

### 3.4 Pre-registration — CONFIRMED ABSENT

No pre-registration, registered-report, or commit-before-test discipline in repo or paper. The IR thresholds and `min_count`s are hand-authored; `results.csv` is post-hoc. The compiler is deterministic *given* the IR, but the IR is uncommitted human judgment. This residue is clean.

## 4. ~~The Finding About OKB Itself~~ — REFUTED 2026-06-04

> ⚠️ **THIS SECTION IS REFUTED. Do not quote it as a live finding.** A line audit of the camera-ready PDF (2026-06-04) showed OKB's paper *explicitly* describes its group-level granularity in four places (§VI.B "per-group allocations"; Listing 1 over `allocatedGPUHoursGroupA/B`; Discussion + Conclusion "richer multi-group metrics are expressible within the same framework"; Appendix A worked example). The premise below — "the paper full text states it has no group/aggregate granularity" — is **factually wrong about the prose.** There is no `ser`/`estar` divergence inside OKB on this axis, so the "in-the-wild instantiation of the failure mode" payoff is **withdrawn.** This was the most inflated claim in the 2026-06-03 set and is exactly what a reviewer who opened the PDF would have caught. Text retained, struck, as a cautionary record. Full disposition: `research-note-okb-verification-reconciliation-2026-06-04.md` §1.

~~OKB's paper full text states it has no group/aggregate granularity; OKB's code contains group-level fairness constraints (§3.2). **The paper under-describes its own code.** This is a `ser`/`estar` divergence — declared capability and operative capability disagree — located in the closest prior art, by applying this project's method as specified.~~

~~The significance is modest and specific, and should not be inflated: it is one discrepancy, in one block (`kb_fairness`), found by reading committed shapes. But it bears directly on the project's central premise. A first-line skeptical objection to the whole program is: "is the `ser`/`estar` gap a real, common failure mode, or a distinction invented to motivate an ontology?" The answer is now empirical rather than rhetorical: **the gap appears, unprompted, in a rigorous independent system we did not build.** The failure mode the architecture diagnoses occurs in the wild, in adjacent state-of-the-art, and is detectable by the prescribed method. That converts the premise from "plausible" to "instantiated."~~

~~It also models the discipline rather than asserting it: we claimed declarations should be checked against substrates, and then we checked one.~~

*The discipline still got modeled — just with the opposite outcome: we claimed declarations should be checked against substrates, we checked, and the check killed our own headline. That is the method working, not failing.*

## 5. Net Effect on Positioning

The novelty residue over OKB is **intact and now reviewer-proof**, but re-stated:

1. **Model-band scope** (not "group scope") — OKB has population-group scope but no model-band scope.
2. **Pre-registered executable adequacy predicates** — OKB's adequacy deferral is total (code-confirmed); this is the hole we fill, not a contest we win.
3. **Conflict as a generative first-class object** — OKB has no conflict model at all (set union); withdraw the "we both preserve" framing.
4. **Pre-registration discipline** — confirmed absent in OKB.

Two of these (1, 3) were overclaimed in the prior notes and would have been refuted at review. The code-read is what made them defensible.

## 6. Ceiling and Falsification

**What this audit did:** read the SHACL shapes, schemas, validation engine, IR, and compiler committed to the OKB `main` branch at clone time (2026-06-03, "10 commits," early-stage prototype).

**What it did NOT do:** run OKB's suite; inspect uncommitted or branch work; review all blocks exhaustively beyond fairness/provenance/the compiler MVP; or verify the camera-ready paper text against this prose summary line-by-line (the full-text reading was via fetch, not a line audit).

**Falsified if:** (a) a later OKB revision adds model-band scope, adequacy/warrant checks (beyond self-declared value comparison), or a conflict model — in which case the corresponding residue narrows further or closes; or (b) re-reading the camera-ready paper shows it *does* describe the group-level granularity, in which case the §4 "paper under-describes its code" finding weakens to "paper de-emphasizes" and should be downgraded accordingly. Both are checkable; both should be re-checked before this note's claims become load-bearing in a published related-work section.

---

*This note supersedes: the keystone note's listing of conflict-preservation as shared-with-OKB (withdrawn — OKB has no conflict model), and both the keystone and positioning notes' claim that OKB has no group granularity (corrected — OKB has population-group, not model-band, scope). Companion: `positioning-correction-2026-06-03.md`, `research-note-structural-vs-semantic-keystone-2026-06-03.md`. OKB repo audited: github.com/AasishKumarSharma/open-knowledge-blocks.*
