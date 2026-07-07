# Research Note: H-A — Forced Grounding Relocates the Parametric Leak from Resolution to Record-Coverage (a bounded trade, not a closure)

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** 2026-06-04
**Method:** Opposed adversarial construction. For each of six structurally distinct classes of omittable feature, an A-prover built a record-only detector and a B-prover built an omitted-correcting feature provably evading any record-only detector; a per-class adjudicator declared A / B / BOUNDARY after cross-attack, and a final adjudicator applied a corridor veto (return "no new seam" if the result is just the keystone-Goodhart diagonal at a new layer). Built to *decide*, not to reach the author-preferred conclusion. (Workflow `ha-forced-grounding-relocation`, 20 agents.)
**Status:** ⚠️ **HEADLINE RETRACTED 2026-06-04 (same day), see §0.** The "new seam (coverage-not-resolution)" claimed below does NOT survive a value-neutering adversary; it dissolves back into the keystone-Goodhart corridor it claimed to be distinct from. The note is retained as a record of the claim and its same-day refutation (deaths before review, not at it). What survives is narrower than §3–§5 assert; read §0 first, then the body as the superseded original.
**Provenance of the seam:** the only runnable open door (H-A) in `research-note-session-synthesis-and-three-falsifications-2026-06-04.md` §4 and `research-note-three-falsifications-joint-2026-06-04.md`. Design: `docs/superpowers/specs/2026-06-04-HA-forced-grounding-relocation-design.md`.

---

## 0. Same-day retraction of the headline (two converging attacks)

The original headline (§3) was: forced grounding RELOCATES the leak from *resolution-opacity* (the Goodhart corridor) to *record-COVERAGE* — a **new, distinct seam**. Two independent attacks, run the same day against this note, converge on killing exactly that distinctness claim. They agree, which is why I trust the kill.

**Attack A — value-neutering adversary (knob-forgeability pass).** The strongest *new* leg, Class 5, detected curation-leak as a population suppression signature `presence-rate(W|majority) ≫ presence-rate(W|minority)` over Σ's logged *surfaced-feature-names*. But a rational adversary suppresses by **value**, not by name: retrieve `W` honestly, log its name honestly (signature stays FLAT and truthful — no forgery, no hidden identifier), and zero `W`'s weight *inside `f`* for the minority (`weight_W = 1.0 if majority else 0.0`), or inject a stale/sentinel value. This produces a leak with **Class-5-identical name statistics and a Class-6 value-local mechanism.** The Class 5 ↔ Class 6 boundary — the note's entire "coverage vs resolution" seam — **is not adversary-stable.** It was an artifact of assuming suppression-by-name. The load-bearing falsehood the note never closed: `name-surfaced(W) ⟹ value-of-W-materially-entered-f`. Name-membership and value-influence are independent variables the policy controls separately. The corridor veto in §3 checked the wrong adversary (name-clumsy, not value-neutering).

**Attack B — governance HMDA-RI 2022 trimodal result** (`governance/docs/superpowers/specs/2026-05-14-hmda-trimodal-replication-result-note.md`, real run, 25,014 rows). Two empirical facts attack the *decidable* tier:
- **Adequacy floored by substrate.** On HMDA most cells are "both inadequate" — `R²_named` runs so low that the same 0.30 predicate threshold "produces different scoring physics." A `fail→pass` branch can be **structurally present in `P`'s text and operatively dead on the substrate.** So §4's "decidable" legs (Classes 1, 3) are decidable *about `P`'s text*, NOT about whether the correction is operative on this substrate — exactly the ser/estar gap the project exists to name, re-imported into my own detector.
- **`purchaser_type` leak** (pre-reg correction #3): a named, present, admissible-*looking* feature (100% of denials carry code 0) re-encoded the label. **Persisted-in-the-record did not imply means-what-you-think.** My separating principle's sufficient condition (name/presence-rate persisted ⟹ detectable) is necessary-not-sufficient: coverage is not innocent.

**What actually survives (smaller than §5):**
- The **irreducible-B core** (Class 6 value-locality; Class 4 on non-separable substrates) — and it is *larger* than the body claims: the attacks show much of the purported A/estimable gradient was Class-6-in-disguise under a competent adversary.
- The **honest-concession content**: the corridor leg loses where it appears; Falsification #1's "closes the leak" is refuted; CONFORMING is never a clean bill of health. These never relied on the retracted seam.
- A **genuinely new and surviving design obligation** (the one durable thing this chase produced): an audit record's surfaced-NAME log is worthless against a value-neutering adversary; closing the leak requires attesting per-row **value-influence** of `W` on `f` — which in faithful form *is the forbidden counterfactual*, so it collapses into the hard-B core, and in estimable form inherits all the gameability of post-hoc attribution. **Name-coverage ≠ value-influence-attestation, and only the latter touches the real threat model.** This is the corrected residue; it is a *tightening* of the irreducible core, not a new seam.

The rest of this note (§1–§7) is the **superseded original**, retained verbatim.

---

---

## 1. The question

Under **retrieval-conditioned forced grounding**, Decision = `f(R)`, where `R` is a declared, finite evidence set; weights may select/combine `R` but the decision cannot route on any applicant feature absent from `R`. Falsification #1's flattering reading was that this *closes* the parametric-leak axis. H-A asks: does forced grounding **eliminate** the leak (Outcome A: relocated-but-record-detectable) or merely **relocate** it opaquely (Outcome B: detection requires the forbidden counterfactual `R′ = R ∪ {W}`, rerun, compare)?

The formal pivot: for a feature `W` **available** and **correcting** (its inclusion would re-route a wrongly-denied qualified applicant toward approval) but **omitted** from `R`,

> `detectable(W)` := ∃ a total function of the **audit record alone** — `ρ = ⟨R, P, Σ⟩` (the evidence set, the pre-registered predicate, the band's observed I/O log) — that flags `W` as available-correcting-omitted *without evaluating `f` on any input not already in `Σ`.*

## 2. The kill-condition fired — conditionally — and the conditioning is the result

If "correcting" is defined as **C-counterfactual** (`f(R∪{W}) = approve` while `f(R) = deny`), detecting it is logically inseparable from running the counterfactual, so B wins trivially and the question is malformed. The formalization confirmed this fires under the natural reading — **but not unconditionally.** A genuine counterfactual-free surrogate exists, **C-record**: read corrective role off `P` symbolically (does `P` have a `fail→pass` branch gated on `W`?) or off an existing `Σ` log entry — neither evaluates `f` on a new input.

**So the question is well-posed, and its non-trivial content is exactly the gap between C-counterfactual-true and C-record-certifiable.** `detectable(W)` holds for features whose correction `P` pre-names or `Σ` pre-witnesses; it provably requires the counterfactual for features whose correction is *true-but-`P`-silent-and-`Σ`-mute*. The verdict is therefore a **split**, located by *which feature classes fall on which side*.

## 3. The seam: detectability tracks record COVERAGE, not predicate RESOLUTION

This is the finding, and it is **not** the keystone-Goodhart corridor. The corridor's opacity is *resolution-limited* (a sub-cell finer than `P`'s partition `Π_P`, invisible to `P`). The corridor leg appears in every feature class here — and **loses wherever it appears**: it is conceded and killed in Classes 2 and 5, is the literal opposite of Class 1's win, and is the *only* genuine corridor-rerun (Class 4, where its own adjudicator notes it "moves the A/B line zero inches"). The verdicts are decided **elsewhere** — on a new axis the weights-only/`P`-only Goodhart framing never used:

> **Separating principle.** The leak is **record-detectable** iff the corrective fact's *name* or *presence-rate* is persisted in the record (`P`'s schema, `R`'s schema, or `Σ`'s per-row logged input topology). It is **counterfactual-only** iff *only the corrective fact's unretrieved value* would distinguish harm from harmlessness, and that value lives off-record.

The opacity that matters is **observation-limited** (a missing scalar value on a variable `P` may even name at full resolution), not resolution-limited. Different opacity class → new seam. The corridor veto did **not** fire (justification: the *winning leg* per class is orthogonal to the unnamed-sub-cell diagonal; the corridor shows up only to lose).

## 4. The six classes and the claim ladder

Reported on a deliberately conservative ladder — **decidable** (exact record-function), **estimable** (powered statistical test, sample-bounded), **counterfactual-only** (forbidden rerun required). The new seam holds at the estimable tier and above; it is **not** oversold as everywhere-decidable.

| Class | Verdict | Tier | What decides it |
|---|---|---|---|
| 1. P-named threshold corrector (e.g. compensating-income doc, FNMA-separable) | BOUNDARY | **Decidable** (recall flag) | A flags "omission worth checking" by static partial-eval of finite `P` + arithmetic on `R`'s named scalars — *no rerun*. Confirmation (B-side) still needs the pulled doc + rerun. Forced grounding helps at the **suspicion** layer, not the confirmation layer. |
| 2. `Π_P`-subresolution corrector (finer-than-predicate proxy) | BOUNDARY | Estimable / counterfactual | Flips on **retrieval-policy `W`-blindness** over the cell. Non-`W`-blind → cheap `Σ` lookup (A). Uniformly `W`-blind → counterfactual (B). The `(ii)` corridor leg is dead by definition; the live axis is policy coverage. |
| 3. Silent-magnitude corrector (`P` names `W` at wrong granularity) | BOUNDARY | **Decidable** if instrumented | Flips on whether a **dispute/correctability field** is in `R`'s schema. One declared field closes the leak (A); absent it, only the real-world rescore + rerun certifies (B). |
| 4. Behaviorally-witnessed corrector (`Σ`-logged analog) | BOUNDARY | Decidable (free) / counterfactual | **The one true corridor-rerun.** Flips on `Π_P`-completeness = separability (keystone §5 verbatim). Separable → A *for free* (`Σ` already ran the counterfactual on an analog — read the flip off the log). Non-separable → B. Contributes an efficiency note, **no new boundary location.** |
| 5. Retrieval-policy systematic omission (curation leak — the H-A target) | BOUNDARY | **Estimable** | A wins on the record-as-written: a **population suppression signature** (presence-rate(`W`\|majority) ≫ presence-rate(`W`\|minority) on `P`-coarse-matched cells) is visible in `Σ`'s logged input *schemas*. B reclaims it only on a *transient identifier never persisted to `Σ`*. The winning leg is **estimable, not decidable** — a powered test, not an exact certificate. |
| 6. Off-record value-local corrector (`W` named nowhere in `P` or `Σ`) | **B** (flat) | **Counterfactual-only** | The irreducible floor. Survives even handing the detector `W`'s name *and* letting `P` reason symbolically — the blindness is to an unretrieved *value*, not an unnamed cell. No record-only function separates harmful from harmless omission. |

## 5. What it reorganizes — and what it does NOT

**The "two-axis impossibility result"** (`ontology-positioning-state`, the #1×#3 pincer) had the second axis as *"parametric/curation leak — not cheaply closeable."* H-A **splits that axis into a coverage gradient.** It is not a single opacity:

- Three named **instrumentation knobs** each move a class from B to A: (1) log the *value* of `P`-named retrieved variables (Class 1 confirmation); (2) persist per-row retrieval coverage / surfaced-feature-names + the keyed identifier (Classes 2, 5); (3) enrich `R`'s schema with a correctability/dispute field (Class 3).
- The residual **hard-B core is narrow and characterized**: Class 6 (value-locality) and Class 4 on non-separable substrates (sub-`Π_P` proxy).

So *"not cheaply closeable"* becomes: **"closeable at a stated record-instrumentation cost, except at the value-locality / sub-`Π_P` limit, where it is closeable in principle only by the forbidden counterfactual."** The headline shrinks from "leak as opaque as weights" to **"leak relocated to a finite, instrumentable record surface with a small irreducible off-record core."** Smaller, truer, more robust.

**Symmetric kill (do not miss this):** the analysis refutes **Falsification #1's flattering reading too.** "Forced grounding *closes* the leak" is as dead as pure-B — Class 6 and non-separable Class 4 are irreducible. Both extremes fall; the truth is a bounded trade. This matters because #1 was the contaminated, prior-confirming result; H-A neither rescues nor buries it — it bounds it.

## 6. Load-bearing assumption and falsification surface

**Load-bearing assumption.** The record model: `Σ` is a **population** log of per-applicant (input-schema, decision) rows, and `R`/`P` expose their named variable topology. *Every* A-win and B→A flip is purchased by something being **in** this record. If `Σ` is instead a single-applicant or non-persistent observational trace, the population-statistical legs (Class 5 especially) evaporate and the result collapses toward flat Outcome B — Class 6 everywhere. **The seam exists iff the record is instrumented; it is a claim about audit-record design, not about forced grounding alone.**

**How a hostile reviewer breaks this (four ways, all conceded here):**
1. **Estimable-vs-decidable.** The strongest *new* leg (Class 5 suppression signature) is a powered test, not an exact certificate. *Response:* §4's ladder concedes this up front; the relocation claim (resolution→coverage) holds at the estimable tier and the static legs (Classes 1, 3) are exactly decidable, so the seam does not depend on the soft leg.
2. **Record-model smuggling.** Every A-win quietly enriched the record beyond a minimal `ρ`. *Response:* true and **stated as the load-bearing assumption** — the contribution *is* "here is which instrumentation buys which detectability tier," not "forced grounding is free."
3. **Separability contamination.** Class 4's A-side and the FNMA framing ride the *same* separability carve-out the project already owns (keystone §5). *Response:* conceded — Class 4 is flagged as the corridor-rerun and explicitly **not** counted toward the new seam.
4. **Root contamination.** H-A is the #1 seed; memory line 37 tags forced grounding as the self-promoting result; "forced grounding converts the leak into a visible trade" flatters that prior, and the analyst was told to resist B — so landing on "A-as-a-trade" is the prior-confirming shape to distrust. *Response:* see §7.

## 7. Contamination disclosure (most credible where it concedes)

H-A is the direct #1-forced-grounding seed. The conclusion "forced grounding converts the leak into a visible trade" flatters the author's own adjacent construct — exactly the result-shape `ontology-positioning-state` line 37 warns to distrust. The discipline that follows: **the result is most credible where it concedes and least credible where it flatters.**

- **Most credible (concessions):** the corridor leg loses everywhere; Class 6 is flat irreducible B; Class 4 is a true corridor-rerun contributing no new boundary; Falsification #1's "closes the leak" reading is refuted.
- **Least credible (flatters):** the "A helped / trade" framing and the breadth of the B→A gradient. Discount the A-lean accordingly.

Every B→A flip is purchased with a record-instrumentation commitment paid at retrieval-**curation** time, not audit time; its cost is qualitative here ("a named field," "per-row names"), **not quantified** — a stated debt, not a hidden one.

---

*Companion to `research-note-three-falsifications-joint-2026-06-04.md` (#1 seed) and `research-note-keystone-goodhart-collapse-2026-06-04.md` (the corridor this note shows it is NOT). Load-bearing empirical assumption — that the audit record persists population-level per-row retrieval topology — is stated in §6 and is the falsification surface for this note itself. Construction is synthetic and adversarial.*
