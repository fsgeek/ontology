# Research Note: Three Falsifications — Joint Reading (#1 HELD, #2 INDETERMINATE, #3 FALSIFIED)

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** 2026-06-04
**Method:** Three parallel falsification attempts (forced-grounding / silence-upstream / ZK-cost), each a structured break-attempt, synthesized for JOINT reading per PI direction (disagreement is the signal; none-falsified would trigger an analysis-error hunt).
**Status:** Result note. Companion to research-note-session-synthesis-and-three-falsifications-2026-06-04.md (the framing) and research-note-keystone-goodhart-collapse-2026-06-04.md (the keystone under attack).

---

# Three Falsifications: Joint Reading — 2026-06-04

## 1. Verdict table

| # | Attempt | Verdict | One line |
|---|---------|---------|----------|
| 1 | Forced-grounding / parametric leak | **HELD** | Separability constrains the allocation map but is structurally blind to the feature scalar fed into it; A/B pair with identical predicate-satisfaction and loss can still diverge in disparate impact. Kills the strong-keystone headline on the parametric-leak axis. |
| 2 | Silence-upstream | **INDETERMINATE** | The deciding experiment (estar population on Olorin FM under silence-intact conditions) was **not run**. Theoretical boundary analysis flags it as high-risk-for-falsification, but the informative fact is non-execution. |
| 3 | ZK construction-provenance cheaper than post-hoc audit | **FALSIFIED** | Dies twice independently: prover work is Θ(training-compute) with 100–1000× constant (super-linear, not sub-linear), AND it proves a disjoint proposition (provenance ≠ fairness) — you can ZK-prove you faithfully ran a discriminatory policy. |

## 2. The JOINT reading — where they DISAGREE

These three do **not** sit in one happy picture. The tension is real and it is the most valuable output of the round. Name it plainly:

**#1 and #3 point in opposite directions about where certification value lives.**

- **#1 (HELD) pushes the burden DOWNSTREAM into the weights.** Its whole force is that observable audit artifacts (allocation feasibility + tree topology over named features) do **not** pin the effective scalar entering the FICO node, because that scalar is an upstream function of unconstrained pretraining weights. The only thing that can close that gap is a **construction-side attestation** (forced grounding: "no decision-relevant fact reaches the scalar except through documented retrieval"). #1's `if_it_holds` is explicit: the auditor obligation must become *certify separability AND certify forced grounding*. **#1 increases the demand for a construction-provenance mechanism.**

- **#3 (FALSIFIED) attacks the economics of exactly that construction-side mechanism** and, more damagingly, proves it is **necessary-not-sufficient**: ZK construction-provenance "proves you ran what you committed" and says nothing about disparate impact. So the mechanism #1 just made load-bearing is the same mechanism #3 demonstrates cannot, by itself, certify the absence of disparity.

**The composition is a pincer, not a contradiction — and it is bad news for the keystone, not good.** Read together:

1. #1 says: separability alone does not certify no-race-disparity; you also need a forced-grounding attestation on the feature-construction layer.
2. #3 says: the natural cryptographic instantiation of that attestation (zkPoT) is (a) expensive and (b) proves the wrong proposition — it certifies *conformance to a policy*, not *fairness of the policy's outputs*.
3. Therefore the second precondition #1 demands is **not a free closure**. It either costs a forced-grounding *architecture* (a real engineering commitment, not a proof you can bolt on) or it inherits #3's necessary-not-sufficient gap. **Closing the allocation axis (separability) and closing the parametric axis (forced grounding) are two different kinds of work, and the second is not certifiable by the cheapest available tool.**

**Where does #2 sit in this picture?** #2 is the load-bearing unknown that decides whether the two projects are *one* line or *two*. Its hypothesis — silence-manufacture is upstream of granularity-collapse — rhymes structurally with #1's parametric-leak channel: both are claims that **the harm enters at a layer the audit observables do not reach** (weights for #1, manufactured-silence / produced-absence for #2). If #2 HELDs, the program collapses to a single causal line in which *the thing you must certify is always upstream of the thing you can observe* — which is exactly #1's finding generalized, and exactly the gap #3 says crypto cannot cheaply close. **If all three resolved the way #1 did, the unified picture would be: every certification target in this program lives upstream of its audit surface, and no cheap mechanism closes the gap.** That is a coherent picture — but it is a picture of a *harder* problem, not a vindicated keystone.

The single sentence that holds all three: **the program keeps discovering that its certifiable surface (allocation, topology, retrieval-conformance) is systematically blind to its actual harm surface (the upstream scalar, the manufactured silence, the policy's disparate impact) — and #3 shows the obvious tool for closing that gap is both costly and aimed at the wrong proposition.** They agree on the *shape* of the problem (upstream blindness) and disagree on whether any current mechanism resolves it (#1 demands one, #3 denies the cheap one).

## 3. None-falsified alarm check

**The alarm does NOT fire.** #3 was cleanly falsified on two independent grounds with numbers from the closest published analog (ZKBoost on the exact credit-default dataset family). One genuine break is present, so we are not in the "everything confirmed what we wanted" failure mode. Good.

**But the PI's instinct still has a target here — the suspicious result is #1 (HELD), and you should treat its cleanliness with care:**

- #1 is the result *the program wanted in a specific way*: it kills a headline (the strong keystone) while simultaneously **re-centering the whole enterprise on forced grounding**, which is the program's own preferred construct (rashomon methodology §1). A falsification attempt that lands precisely on "you need MORE of the thing I was already selling" is exactly the shape of a result that confirms a prior. The break demotes separability but *promotes the author's adjacent commitment*. That is the tell to watch.
- **Where the analysis error would most plausibly hide in #1:** its own `ceiling`. The construction assumes the credit-risk scalar is routed through learnable weights the model can reshade. #1 concedes that if FICO is an immutable retrieved bureau number, the channel is **closed on that feature**. On FNMA-conforming single-family — the exact substrate the keystone note (§5) and #2's boundary analysis both pin as threshold-eligibility with a Desktop-Underwriter-style classifier — the headline decision inputs (FICO, DTI from documented income, LTV) are substantially *retrieved bureau/document pulls*, not free model-computed scalars. So #1's "blindness in principle" is real but its *binding* on the actual keystone substrate rests on the antecedent "this deployment routes the credit-risk scalar through learnable weights." **If that antecedent is false on FNMA-standard underwriting, #1 establishes a general-principle blindness that does not actually fire on the substrate the keystone was scoped to** — the same way the Goodhart counterexample was shown (keystone note §5) not to fire on FNMA. That is the place to push: does #1 demote the keystone *on FNMA*, or only on substrates with model-computed decision features? The two are very different damage reports, and #1's confidence ("the antecedent is not contrived") is doing the load-bearing work that should be checked empirically, not asserted.

So: not an alarm, but a flag. #1 is the result most likely to be partially an artifact of its own scoping, and its sharpest version (kills the keystone *on FNMA*) is the version it has **not** earned yet.

## 4. Next hypotheses — the doors the breaks opened

**H-A (from #1's seed — retrieval-set curation leak; highest priority).** Forced grounding does not eliminate the leak, it *relocates* it. Test: a fully forced-grounded model on a separable FNMA substrate, where every decision-relevant fact flows through documented retrieval, **still admits race-disparate outcomes via retrieval-set curation** — an omitted-but-available feature that would have corrected a race-correlated retrieved feature is a leak the audit cannot see (failure mode (c), promoted from weights-layer to retrieval-policy layer). Falsified if any race-disparate outcome under forced grounding is detectable from the retrieval policy specification alone. This is the direct continuation of #1 and the one that decides whether forced grounding is a *fix* or a *relocation*.

**H-B (the #1×#3 pincer made concrete — does the second precondition have ANY cheap certificate?).** #1 demands a forced-grounding attestation; #3 kills the cheap crypto version *as a substitute*. Open question #3 explicitly left alive: **the marginal/fleet-scale story.** Is the per-model *incremental* zkPoT cost (folding one new model's training trace onto a once-committed policy) below the per-model post-hoc audit cost? Even if yes, "inverts adoption" stays dead and it stays a complement — but "pays for itself at fleet scale" survives and should be isolated from the per-proof claim that just failed. Run the per-model-marginal comparison against ZKBoost-style numbers; report the sign, not a dollar figure.

**H-C (run #2 — it is the cheapest high-value experiment on the board).** #2 is INDETERMINATE only because it was never executed. Execute the estar-population attempt on the Olorin FM case under silence-intact conditions. Falsified if ser/estar is populatable and non-contradictory without silence-breaking. If it survives, immediately run the **substrate-specificity check** (#2's own seed): reproduce across LC pricing and HMDA-RI. If the ser/estar gap reproduces across substrates, the one-causal-line claim is universal; if it fails on some substrate, it narrows to substrate-conditional. **This is the experiment whose non-execution is currently the largest unknown in the joint picture** — it decides one-line-vs-two-lines, which is precisely what Section 2's tension turns on.

## 5. Net effect on the program frame

**Two claims killed, separability demoted, one decisive experiment still unrun. The contribution has gotten SMALLER in headline and DIFFERENTLY-SHAPED in substance — and that is a stronger position, not a weaker one.**

What died:
- The **strong-keystone headline** ("CONFORMING certifies no race-disparate outcome on a separable substrate") — killed by #1 on the parametric-leak axis. Separability is demoted from *sufficient* to *closes only the allocation axis*.
- The **economic adoption argument for ZK** ("commitment pays for itself / cheaper than the audit it replaces") — killed by #3. ZK construction-provenance is re-anchored as a *confidentiality/disclosure* benefit and a *necessary-not-sufficient complement*, never a substitute or a cost-saving.

The strongest defensible statement of the contribution now:

> **On a separable, threshold-eligibility substrate, audit-observable conformance (allocation feasibility + named-feature topology) certifies that allocation is not slot-rationed and that named features appear in the decision — and nothing more. It is structurally blind to disparity manufactured upstream of the audit surface (in feature-construction weights, in retrieval-set curation, or in manufactured silence). Closing that upstream axis requires a second, construction-side attestation (forced grounding), which is a distinct engineering commitment — and the cheapest cryptographic instantiation of it (zkPoT) is both super-linear in cost and aimed at the wrong proposition (it certifies conformance, not fairness).**

That is a **two-axis impossibility-shaped result** (allocation axis closeable by separability; parametric/curation/silence axis NOT closeable by any current cheap mechanism) replacing a **one-axis sufficiency claim** that has now been falsified. It is narrower, more honest, and far more robust to a hostile reviewer — the reviewer with the ZKBoost numbers and the parametric-leak construction is now *inside* the contribution rather than waiting to demolish it.

**Two caveats that keep this honest:**
1. The smaller frame is only fully earned once **H-C runs**. The "two parallel lines vs one causal line" question (Section 2) is unresolved, and #2's non-execution is the single largest gap in the joint picture.
2. #1's damage report has two strengths and the program should claim only the one it earned. "Blindness in principle" is established. "Demotes the keystone *on FNMA-standard underwriting specifically*" is **not yet established** — it depends on the unverified antecedent that FNMA deployments route the credit-risk scalar through reshadeable weights rather than fixed bureau pulls. Claim the principle; flag the FNMA-specific version as pending the same kind of substrate check that has already shown other counterexamples not to fire on FNMA.

Files referenced: `/home/tony/projects/ontology/research-note-session-synthesis-and-three-falsifications-2026-06-04.md`, `/home/tony/projects/ontology/research-note-keystone-goodhart-collapse-2026-06-04.md`, `/home/tony/projects/ontology/rashomon-routed-decision-methodology.md`, `/home/tony/projects/ontology/research-note-layered-ontology-strawman-2026-05-13.md`, `/home/tony/projects/ontology/research-note-variant-indexical-silence-manufacture-result-note.md`, `/home/tony/projects/ontology/position-section3-underwriting.md`, `/home/tony/projects/ontology/2026-05-25-next-experiments-plan.md`