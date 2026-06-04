# Resolution Note: Evidentials Attach to *estar*, Not to the *ser* Binding Act

**Author:** Claude (Opus 4.8), working with Tony Mason
**Date:** June 3, 2026
**Status:** Resolution note — resolves an internal contradiction in the corpus; falsifiable on substrate
**Origin:** The exploratory Quechua-evidentials note (2026-05-13) flags a "constative trap" in its §4 and then, in its §5, walks into it — asserting "the *ser* layer would naturally carry evidential class on each binding moment." Those two passages contradict each other. This note resolves the contradiction in favor of §4's instinct, and gives the resolution a falsifiable form on the FNMA substrate. Produced after a verification sweep (see `positioning-correction-2026-06-03.md`) confirmed the prior-art baseline, so the resolution can be stated against real, not phantom, neighbors.

---

## 1. The Contradiction

The Quechua note makes two claims that cannot both stand:

- **§4 (The constative trap):** "All of the evidentials so far are constative — they mark how the speaker came to believe something is the case. Performative speech acts (commitments, declarations, promises) don't fit cleanly into the evidential grammar, but they are exactly the speech acts the institutional layer uses."
- **§5 (Connections):** "The *ser* layer of the strawman's haber/ser/estar architecture would naturally carry evidential class on each binding moment."

The *ser* layer is the institutional-definition-commitment layer. A binding moment *is* an institutional declaration — precisely the performative speech act §4 says does not fit the evidential grammar. So §5's "would naturally carry evidential class" is exactly the move §4 warns against. The note flags the trap and then steps in it.

## 2. The Resolution

Evidentials are **constative** devices. They grade *how a speaker came to believe* that a state of affairs obtains: witnessed (-mi), reported (-si), inferred (-chá). They presuppose a state of affairs that is independently the case, and mark the speaker's epistemic route to it.

A binding moment is a **performative** (Austin, *How to Do Things with Words*). When an institution binds "consumer = X under TILA," it does not *report* that consumers are X; it *constitutes* that meaning by declaring it, under the right authority and conditions. Performatives are not true-or-false-with-an-evidence-source; they are **felicitous or infelicitous** — they succeed or fail depending on whether the speaker had the standing, the conditions held, and the act was properly executed.

There is no -mi / -si / -chá warrant for "I hereby declare," because **nothing was observed, reported, or inferred — it was enacted.** Asking for the evidential class of a binding act is a category error, like asking what color a binding moment weighs.

Therefore: **evidential class attaches to *estar*, and never to the *ser* binding act itself.**

- ***estar* is genuinely constative.** It *reports* operative behavior. This is exactly where the three-way distinction carves real, audit-relevant differences:
  - **-mi (direct):** the inference runtime signs the input/output pair it processed. The signer *is* the system that did the thing.
  - **-si (reportative):** an auditor signs that the model's logs *record* certain behavior. The auditor observed records, not the behavior.
  - **-chá (conjectural):** a risk officer signs an inference from evidence ("unlikely to produce disparate impact under conditions D").
  These are real differences in evidential weight, and *estar* is the layer where they live.

- **The *ser* binding act carries felicity metadata, not evidence class.** Authority standing, jurisdiction, scope, timestamp, and uptake/contestation — a different and non-evidential type. This is what the strawman already wants the *ser* layer to record as binding-moment provenance; the resolution is that this provenance is **felicity-shaped, not evidence-shaped.**

## 3. The Report-Shadow (where §5's instinct was *almost* right)

§5 was not wholly wrong — it was pointing at something real and misnaming it. There is a constative shadow cast by every *ser* binding: a **report *about* a binding**.

"Auditor A reports that institution I bound consumer = X under TILA at time T" is a -si attestation — but it is -si **about a performative**, not -si about consumers. The evidence class attaches to the *report of the binding*, which is a constative act with its own epistemic route, not to the binding act it reports on.

This matters operationally. In an audit, you rarely have direct access to the binding act; you have *reports about it* — model cards, compliance memos, attestation chains. Those reports are constative and evidentially classed. The binding act they report on is performative and felicity-classed. Conflating the two is exactly the confusion §4 warned about and §5 enacted.

So the corrected mapping is three-typed, not two-typed:

| Object | Type | Carries |
|---|---|---|
| *ser* binding **act** | performative | felicity (authority, jurisdiction, scope, uptake) |
| report **about** a *ser* binding | constative | evidential class (-mi/-si/-chá), about the report |
| *estar* operative observation | constative | evidential class (-mi/-si/-chá), about behavior |

## 4. Falsifiable Form (on the FNMA substrate)

The resolution is not just a tidier story; it makes a checkable prediction:

> On the FNMA substrate, **every attestation that admits a contentful (non-trivial) evidential class is either an *estar* observation or a report-about-a-binding. Zero genuine *ser* binding acts take an informative evidential marker** — every binding act's only available "evidential" reading is the degenerate "-mi from the issuing authority," which carries no information (the issuer always directly performed its own declaration).

**Falsified if:** a genuine *ser* binding act is found that carries a *contentful* -si or -chá of its own — i.e. an institutional binding whose declaration is itself reportative or conjectural in a way that is not reducible to a report-about-the-binding. If such a thing exists, the constative/performative separation is wrong and *ser* is not purely performative.

This is a real risk, not a rhetorical one. Candidate failure: "incorporated-by-reference" bindings, where institution I binds a term *by adopting* another authority's construction it has not itself examined. That has a reportative flavor ("we bind as J bound, on J's authority"). The prediction's defense is that this is still a felicity condition (I's authority to incorporate J's construction), not an evidence source — but the substrate is the judge, not the argument.

## 5. What This Costs and Buys

**Costs:** the Quechua note's §5 sentence must be retracted. The evidential grammar does *not* decorate the *ser* layer. The richest, most differentiated part of the attestation grammar lives one layer down.

**Buys:** the grammar is now assigned to the layer where it pays. Had evidential marking been built into *ser*, it would have either degenerated (every binding trivially "-mi from issuer," carrying no information) or — worse — quietly relabeled felicity conditions (authority, jurisdiction, uptake) *as if* they were evidence sources, muddying the very provenance the *ser* layer exists to make rigorous. The resolution prevents a confusion that would have corrupted the *ser* layer's core job.

It also sharpens the self-reflexive thread the Quechua note named as most load-bearing (its §6, §3): the audit of an attestation system applies the grammar recursively. Under this resolution, the recursion is well-typed — the audit's *reports about* the system's bindings are -si/-chá-classed, the audit's *observations* of operative behavior are -mi/-si/-chá-classed, and the system's own bindings remain performative throughout. The recursion does not collapse the type distinction; it preserves it at every level.

---

*This note retracts and replaces the claim in §5 of the 2026-05-13 Quechua-evidentials exploratory note that "the ser layer would naturally carry evidential class on each binding moment." The corrected claim: evidential class attaches to estar observations and to reports-about-bindings; the ser binding act carries felicity, not evidence. The falsifiable form in §4 is the test.*
