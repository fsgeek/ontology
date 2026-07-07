# Design: H-A — Does forced grounding eliminate the parametric leak, or relocate it?

**Date:** 2026-06-04
**Author:** Claude (Opus 4.8) with Tony Mason (PI)
**Status:** design, approved structure pending spec review

## The claim under attack

Under **retrieval-conditioned forced grounding**, Decision = f(R), where R is a
declared, finite evidence set. Weights cannot route the decision on applicant
features absent from R. The flattering reading of falsification #1 is that this
*closes* the parametric-leak axis. H-A attacks that reading.

## The formal pivot

For a feature W that is **available** and **correcting** (its inclusion would
move the decision toward a wrongly-denied qualified applicant) but **omitted**
from R:

> `detectable(W) := ∃ a function of the AUDIT RECORD ALONE — R, the
> pre-registered predicate P, and the band's observed behavior — that flags W
> as available-correcting-omitted.`

- **Outcome A (relocates-but-auditable):** `detectable(W)` holds. Forced
  grounding *helped* — it converted an opaque parametric leak into a visible
  omission in a declared finite set. Keystone survives, stronger; design
  obligation becomes "audit the omissions in R," which is checkable.
- **Outcome B (relocates-opaque):** detection provably requires the
  counterfactual (build R′ ∪ {W}, compare outcomes). Leak moved to a surface as
  opaque as weights were. "Not closeable in principle" — the bigger claim.
- **Expected real finding: the BOUNDARY.** Some feature classes land in A, some
  in B. The deliverable is the characterization of the boundary, not a single
  verdict.

## Contamination guard (load-bearing)

The fun-compass pulls toward B (cleaner, bigger, quotable). #1 was contaminated
by flattering the author's own forced-grounding construct; the mirror risk is
that H-A flatters "not closeable in principle." Guard: build the construction to
**decide** A vs B, never to reach one. Two opposed adversaries:

- **A-prover:** for a feature class, construct the record-only detector.
- **B-prover:** construct an omitted-correcting W that provably evades any
  record-only detector.

Verdict per feature class = whoever survives the other's strongest attack.
Neither Claude nor the compass picks the answer. **A is the more surprising,
under-sampled outcome and must NOT be treated as the loss.**

## Steps

1. **Formalize** the record and `detectable(W)`. Pin "available" and
   "correcting" precisely enough to decide. *Kill condition:* if "available"
   cannot be defined without the counterfactual, B wins trivially and the
   question was malformed — record that as the result.
2. **A-prover** builds the record-only detector for the broadest feature class
   it can.
3. **B-prover** builds an omitted-correcting W that evades any record-only
   detector.
4. **Adjudicate** the boundary; characterize A-region and B-region; add cost
   texture (A: how cheap is the detector? B: what forces the counterfactual?).

## Failure mode to name explicitly

If the A/B boundary is just a restatement of "named vs unnamed sub-cells" — the
Goodhart diagonal from `research-note-keystone-goodhart-collapse-2026-06-04.md`
in new clothes — then this is the walked corridor at finer grain. The
adjudicator MUST test for this and is empowered to return "no new seam; corridor
re-run" as a first-class verdict.

## Output

`docs/research-note-HA-forced-grounding-relocation-2026-06-04.md`, in the
self-auditing style of the existing notes (states its own load-bearing
assumption and falsification surface). No code — constructive/theoretical,
matching how the project's other results were produced.

## Method

Workflow: opposed adversaries (A-prover vs B-prover) over feature classes, with
adversarial verification of survivors and an adjudication pass that can veto the
whole thing as corridor-rerun.
