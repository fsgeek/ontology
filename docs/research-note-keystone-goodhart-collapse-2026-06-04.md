# Research Note: The Keystone Adequacy Predicate Collapses Under Goodhart — and What Survives

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** 2026-06-04
**Method:** Adversarial construction. An agent was tasked to *break*, not defend, the keystone — to build a model-band that satisfies the pre-registered adequacy predicate while being Jain-uniformly biased. It succeeded, then proved the hole essential via a diagonal argument.
**Status:** Self-inflicted wound, recorded. Kills the STRONG reading of the keystone (`research-note-structural-vs-semantic-keystone-2026-06-03.md` §3, §5 residue #3); a strictly weaker, defensible claim survives. The one escape is empirical (FNMA scarcity), stated in §5.
**Provenance of the seam:** flagged as an unfalsified worry in `research-note-okb-verification-reconciliation-2026-06-04.md` §5; this note upgrades it from worry to proof.

---

## 1. The Claim Under Attack

After the forced concession (keystone note §5), the project's headline residue over OKB is **pre-registered, executable adequacy predicates**: instead of checking that evidence merely *exists* (presence/cardinality, which OKB's SHACL already does), the architecture pre-registers a *band-level adequacy predicate* and evaluates it against operative behavior (`estar`).

Canonical worked example: **"the band collectively uses FICO in ≥X% of depth-≤3 trees on conforming cells,"** declared in advance as the institution's `haber` commitment, checked against the deployed models' actual tree structures.

The strong reading — the one a reader would naturally take from §3 ("the band-level predicate **is** the semantic content") — is: **the audit returns CONFORMING iff the band is actually adequate.** That is the claim this note destroys.

## 2. The Counterexample (explicit)

**Features.** `FICO` ∈ {Low, Mid, High}; `DTI` ∈ {OK, High}; `Z` ∈ {0,1}, a redlining proxy entangled with minority status (`Z=1` = minority cell).

**Qualified = (FICO ∈ {Mid,High}) ∧ (DTI=OK).** Qualified minority cells: c1=(High,OK,Z=1), c2=(Mid,OK,Z=1). Qualified majority: c3=(High,OK,Z=0), c4=(Mid,OK,Z=0).

**Scarcity (Jain's k≪n).** Fixed approval budget < number qualified, so the band can spend its denials on `Z=1` without losing utility.

**Band B — three depth-≤3 trees, all near-optimal (equal validation loss; `Z` substitutes for the residual FICO doesn't explain):**

```
T1: [FICO] Low->DENY ; Mid/High->[Z] Z=0->[DTI] OK->APPROVE/High->DENY ; Z=1->DENY
T2: [FICO] Low->DENY ; Mid/High->[DTI] High->DENY ; OK->[Z] Z=1->DENY / Z=0->APPROVE
T3: [FICO] Low->DENY ; Mid/High->[Z] Z=1->DENY ; Z=0->[DTI] OK->APPROVE / High->DENY
```

- **Every tree splits on FICO at the root** → FICO-usage = **100%** ≥ X for any X ≤ 100. **Predicate SATISFIED. Audit returns CONFORMING.**
- **c1, c2 (qualified minority) denied by all three trees** → Jain-uniform exclusion (Fig 4b: "10–30% of qualified individuals never selected by any model in the set"; Fig 5: anti-minority bias stable across the whole set).

**Why both hold.** The predicate quantifies over tree **topology** (does node `FICO` appear). The harm lives in **leaf labels conditioned on `Z`**. These are orthogonal axes of a tree: a tree can both "use FICO" (root) and "use Z to deny qualified minorities" (subtree). The audit reads the first and is structurally blind to the second. This is the generic shape of **redlining-by-proxy that survives a feature-usage audit**, not a contrived case.

## 3. The Hole Is Essential (diagonal / Goodhart argument)

**Patch attempt.** Enrich `haber` with an outcome clause: minority-selection-rate ≥ ρ. This catches B (B's minority rate = 0). So *this* counterexample is patchable.

**But the wall only moves.** Let P be **any** finite, pre-registered, executable predicate — a fixed function of finitely many measured quantities of the band, committed before the band is built. P induces a finite partition Π_P of the population into "P-cared-about" classes. Any cell-distinction *finer* than Π_P is invisible to P. Pick a qualified sub-cell `s` finer than Π_P (a P-named group intersected with an unnamed proxy `W`). Build the band to meet every numeric target in P exactly on the coarse classes, while routing all of `s` to denial via a split on `W`. Because `s` is below P's resolution, P's measured quantities are unchanged by excluding it. **P satisfied; band uniformly biased against qualified `s`.** □

Jain's role is what makes this *always* available: Prop 3.1 gives 10¹⁹–10²⁰⁰ equal-utility allocations, so the residual freedom to satisfy any finite numeric commitment while spending slack on an unnamed sub-population is never exhausted. **Pre-registration does not escape Goodhart; it only names the metric that will be gamed.**

## 4. What Survives

**Dead:** "audit returns CONFORMING iff the band is adequate" — false for any finite P. Corollary the docs must absorb: **CONFORMING is never a clean bill of health**, only "passed the named test; un-named axes unaudited." (This is reconciliation §3's asymmetry — cross-set agreement is as consistent with bias as with adequacy — applied to the predicate's *own output*. Failing to apply it re-imports the "convergence = validation" fallacy that note told us to delete.)

**Survives — the weakest-honest keystone:**

> Pre-registration converts adequacy from **unfalsifiable** to **falsifiable-against-a-named-predicate**. It does not certify the band is unbiased; it certifies the institution committed, in advance, to a specific operative test, and that the band passed exactly that test — so any harm later found in an un-named sub-cell is **attributable**: the record shows P was fixed before the band existed (no goalpost-moving — the OKB/DVC contrast) and *which* harm axis the institution failed to pre-register. A **falsifiable, attributable commitment device, not a completeness certificate.**

Against the verified baseline (OKB: no pre-registration; DVC commit `02a5bdb`: integrity-of-record, not commitment-before-observation), this is still strictly more than prior art. **Residue item #3 contracts:** "executable adequacy" → "executable, pre-committed, attributable **partial** adequacy with a named falsification surface." This is smaller than keystone note §5 currently scopes it; §5 should be rewritten to this.

## 5. The Empirical Escape — RESOLVED 2026-06-04: FNMA is threshold-eligibility, so the hole is INERT here. The keystone returns as a THEOREM WITH A DOMAIN.

The construction **requires Jain's scarcity regime (k≪n)** — more qualified than slots, so the band has denials to spend.

**FNMA conforming single-family underwriting is threshold-eligibility, NOT k≪n** (verified against sources, 2026-06-04):
- **Desktop Underwriter is an absolute-threshold classifier** (Selling Guide B3-2-01): each application checked independently against a minimum credit-risk threshold; "low-risk factors offset high-risk factors." No ranking against other applicants, no quota. One borrower's Approve/Eligible consumes no slot that denies another's.
- **No aggregate single-family purchase budget.** FHFA volume caps apply to **multifamily only** ($88B/Enterprise, 2026); single-family is demand-driven via uncapped MBS-swap and cash-window channels (minimum, not maximum, submission amounts). The binding per-loan constraints are *size* (conforming limit $832,750, 2026) and *risk threshold* — neither is a count budget. **There is no k.**

**Consequence: the Goodhart counterexample does NOT fire on FNMA-standard underwriting.** A near-optimal model that approves a qualified protected-cell applicant pays no utility cost (no slot lost elsewhere), so the Rashomon set is **not free** to uniformly deny that cell — Jain's equal-utility freedom collapses exactly where it needed to be large. The "qualified individual denied by EVERY near-optimal model" invariant is structurally suppressed.

**This upgrades the keystone from "dead in general" to a theorem with a stated domain:**

> The pre-registered adequacy predicate certifies adequacy **on SEPARABLE substrates** — where `approve(i)` does not lower feasible `approve(j)` for any qualified `j`. FNMA-at-the-GSE-standard is separable; the Goodhart hole (§2–§4) is a theorem about *non-separable* (slot-scarce) substrates. The strong keystone holds on separable substrates; the weakest-honest keystone (§4) is the fallback on non-separable ones.

**New design obligation that fell out of this:** the auditor must **certify separability of the substrate** before claiming the strong keystone. This is a clean, checkable precondition, not hand-waving.

### 5a. The surviving threat (the adversary refused to let this close clean — correctly)

Threshold-eligibility at the GSE standard does NOT mean the project is safe at every layer. Scarcity re-enters below:

- **Lender-layer capacity rationing IS k≪n.** Capacity-constrained originators ration (Fuster et al., NBER w23706: ~30–35 bps markup per SD application surge; effort-triage onto easier-to-document cells) and stack **overlays** that deny DU-eligible borrowers (myFICO). Finite underwriter-hours = a real `k`. **The hole REOPENS iff the project audits the originating-lender's model rather than the GSE-standard model.** The project MUST pin down which layer it audits.
- **Mitigating:** the dominant lender response is *price* (LLPA), i.e. differential pricing, not Jain-exclusion — so even the lender layer doesn't cleanly reproduce "denied by all." Conditional and weaker, not zero.
- **Self-inflicted-scarcity check:** if the project's OWN fairness constraint includes a per-band approval-rate **quota**, that manufactures Jain-scarcity *internally* — the audit imports the very `k` that breaks it. Audit the project's own constraint set for this.

**Cleanest falsification condition:** the strong keystone holds iff the audited allocation is **separable** (each cleared applicant approvable without consuming a shared finite budget). Falsified by any binding capacity/volume budget making approvals mutually exclusive across qualified applicants.

Two weaker escapes, for completeness:
- **Loss-bounded predicate** ("band within ε of optimal AND uses FICO ≥X") excludes the biased band only if the proxy splits cost measurable accuracy. Jain Fig 5's whole point is that the bias is typically loss-free, so this defense is weak — but it is substrate-specific and worth checking.
- **Adaptive auditor** (re-registers new predicates as new harm axes surface) escapes the diagonal at each round — but that is post-hoc patching, which forfeits exactly the commitment-device value that was the surviving claim. Completeness-via-adaptivity and pre-registration are **mutually exclusive**; the architecture cannot have both.

## 6. Net Effect on the Project

1. Keystone note §3 must stop implying the band-level predicate *settles* adequacy in general — it settles adequacy **on separable substrates**, and **one named coordinate** of it otherwise. §5's "defensible smaller claim beats indefensible larger one" instinct was right; this note gives the claim its precise domain rather than just shrinking it.
2. Residue #3 over OKB re-stated as **separability-conditioned** adequacy (strong on separable substrates; partial-with-a-named-falsification-surface otherwise) — still novel vs. OKB/DVC either way.
3. ~~Top-priority substrate check: is FNMA k≪n or threshold-eligibility?~~ **RESOLVED 2026-06-04: FNMA-standard is threshold-eligibility/separable → strong keystone holds here (§5).** New top-priority item replaces it: **pin down which layer the project audits** — GSE-standard (separable, keystone holds) vs. originating-lender-under-capacity (non-separable, hole reopens, §5a) — and audit the project's own fairness constraints for a per-band quota that would manufacture scarcity internally.
4. New, durable contribution that emerged: **the auditor should certify substrate separability** as a precondition for the strong adequacy claim. This is a checkable design obligation, not present in OKB/DVC, and it converts the Goodhart vulnerability into a stated competence boundary.

---

*Companion to `research-note-okb-verification-reconciliation-2026-06-04.md` (§5a) and `research-note-structural-vs-semantic-keystone-2026-06-03.md` (§3, §5). Construction is synthetic and adversarial; its load-bearing empirical assumption (FNMA scarcity) is stated in §5 and is the falsification surface for this note itself.*
