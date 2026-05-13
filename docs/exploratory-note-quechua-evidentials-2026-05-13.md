# Exploratory Note: Quechua Evidentials as Attestation Grammar

**Author:** Tony Mason / wamason.com LLC
**Date:** May 13, 2026
**Status:** Exploratory thinking — not a strawman, not for distribution
**Origin:** Companion to the layered ontology strawman (May 13, 2026). Develops a thread the strawman defers — the proposal that attestation systems borrow grammatical evidentiality from Quechua — separately and speculatively, with explicitly different epistemic status from the strawman.

---

## 1. The Observation

Most attestation systems treat signatures as homogeneous trust tokens. An attestation is signed by an authorized party, the signature certifies the content, the verifier confirms the signature. The system's grammar admits one type of attestation, distinguished only by signer identity, content, and time.

Quechua and several other Andean languages, along with Tibetan, some Caucasian languages, and several Amazonian languages (most famously Tariana), treat the epistemic source of a claim as obligatory grammatical information. In Cusco-Collao Quechua, declarative sentences carry one of three evidential markers, and the marking is not optional:

- **-mi / -n** (direct): the speaker witnessed or directly experienced the event. *Paran-mi* — "It is raining, and I see it."
- **-si / -s** (reportative): the speaker learned of the event from another source. *Paran-si* — "It is raining, I am told."
- **-chá** (conjectural): the speaker is inferring, guessing, or making a probabilistic judgment. *Paran-chá* — "It is raining, presumably."

These are obligatory grammatical structure, not optional rhetorical flourishes. A speaker who fails to mark evidential class is producing an ill-formed sentence, not merely a vague one. The language enforces a distinction English makes only by lexical choice and tonal context, and only when the speaker decides to.

The exploratory question pursued in this note: what would happen if attestation systems made the same distinction obligatory at the protocol level?

## 2. The Proposed Mapping

A regulatory attestation grammar could mark every attestation with one of three evidential classes corresponding loosely to the Quechua three:

**Direct attestation (-mi class).** The signer is the entity that directly observed or performed the attested event. The inference runtime signs the input/output pair it processed. The training pipeline signs the weights it produced. The signing authority *is* the system that did the thing.

Example: *"Inference runtime R produced output O from input I at time T, signed by R."*

**Reportative attestation (-si class).** The signer reports what another source claims. The auditor signs the assertion that the model's logs record certain behavior; the auditor did not produce the behavior, only observed records of it. The compliance officer signs that the model card accurately describes the model; the officer did not build the model.

Example: *"Auditor A reports that, per inference-runtime logs accessed at time T', model M's outputs on test set T match expected pattern E, signed by A."*

**Conjectural attestation (-chá class).** The signer makes an inference, prediction, or normative judgment about something not directly observed. The risk officer signs that the model is unlikely to produce disparate impact under deployment conditions D; this is an inference from evidence, not an observation. The senior officer signs that the model class meets fair-lending standards as currently interpreted.

Example: *"Risk officer R concludes, based on evidence E and policy framework P, that model M's deployment is consistent with TILA's fair-lending requirements, signed by R."*

The three types are epistemically different in ways that matter for audit. The current attestation infrastructure collapses them, requiring auditors to disentangle the evidential class from the content of the attestation by reasoning about who-signed-what. The grammar move pulls this reasoning into the protocol as obligatory metadata.

## 3. Why This Might Matter

The audit question "what is the evidential basis for this claim?" is one regulators ask constantly, usually in indirect form. An attestation grammar that surfaces evidential class as protocol-level metadata makes the question's answer machine-readable.

It also changes the trust calculus. A -mi attestation about a model output, signed by the inference runtime, has very high evidential weight — the system attesting *is* the system that produced the artifact. A -si attestation about the same output, signed by a different system reading logs, has lower weight; failure modes exist (logs can be tampered, log readers can mis-parse, the chain of custody between runtime and audit can break). A -chá attestation about the same output, signed by a human inferring from evidence, has different weight again — bounded by the inferer's competence and the evidence base, with all the messiness human judgment introduces.

Current attestation systems require the verifier to reason about evidential class from context: who is the signer, what kind of artifact is being signed, what is the structural relationship between signer and artifact. The grammar move pulls this reasoning into the protocol, where it can be enforced rather than recovered.

There is also a self-reflexive bite, which is the part that feels load-bearing. The audit of an attestation system is itself a recursive application of the same grammar. A -mi attestation about the attestation chain (signed by the system that ran the chain) is different from a -si attestation about the chain (signed by an external auditor reading the logs) is different from a -chá attestation about the chain ("we believe the chain is intact based on these tests, but cannot directly verify"). Without the grammar, these are easily confused or run together; with it, the audit's own evidential structure becomes part of the visible record.

## 4. Open Problems

**Composed evidentials.** Quechua has rules for what happens when evidential types compose — the marker attaches to the most informationally salient element, and complex sentences can carry multiple evidentials at different scopes. The analog for attestation chains is non-trivial. An attestation chain composed of a -mi attestation about an output, a -si attestation about that attestation, and a -chá attestation about the whole composition has some compositional evidential type that the system must compute, and the rules for that computation aren't obvious. The conservative move is "the chain's evidential class is the weakest link" — a chain ending in -chá is -chá regardless of how many -mi links it contains — but this may be too conservative and may collapse useful distinctions.

**Cross-dialect translation.** This note uses Cusco-Collao Quechua forms. Bolivian Quechua, Ayacucho Quechua, and Northern Quechua (Kichwa) have related but distinct evidential systems with overlapping but non-identical semantics. A formal protocol borrowing this distinction must commit to one analytical schema and explain why. (And the question "which Quechua?" is exactly the metalanguage problem the strawman defers — recursive.)

**Enforcement granularity.** Should the evidential class be enforced by the protocol (the system refuses to verify an attestation without a class marker) or merely labeled (the class is advisory metadata for downstream consumers)? Quechua enforces it grammatically; whether the attestation analog should similarly enforce or merely advise is a design choice with substantial implications for adoption and for the failure modes the system can detect.

**Beyond the three classes.** Several languages distinguish further: hearsay vs. quotative (the latter requires naming the source), sensory vs. inferential, direct-visual vs. direct-auditory, ego-evidential vs. non-ego (Tibetan). Tariana has five distinct evidentials including visual, non-visual sensory, inferred, assumed, and reported. Whether the attestation grammar should adopt the canonical Quechua three or extend further depends on what audit distinctions actually matter operationally — which is an empirical question, not a typological one.

**The constative trap.** All of the evidentials so far are constative — they mark how the speaker came to believe something is the case. Performative speech acts (commitments, declarations, promises) don't fit cleanly into the evidential grammar, but they are exactly the speech acts the institutional layer uses. The relationship between evidentiality and speech-act class needs to be worked out before this becomes operational.

## 5. Connections to Adjacent Work

- **Aikhenvald (2004), *Evidentiality*** (Oxford), is the standard reference for cross-linguistic evidential systems. Quechua is one of her canonical cases; the proposed attestation grammar is essentially a productive borrowing from her typology applied to a domain she did not herself anticipate. The intellectual genealogy is worth tracking.
- **The autobiographer/biographer cliff** from Hamut'ay has an evidential analog. An autobiographer can produce -mi attestations about itself; a biographer is structurally limited to -si attestations about its subject. The finding that autobiographers behave differently than biographers corresponds, in this framing, to "systems where -mi is available behave differently than systems limited to -si." This is not metaphorical mapping — it is the same structural property under different linguistic clothing.
- **The epistemic honesty impossibility result** can be partly re-stated as: text-only observation cannot reliably distinguish -mi-class from -si-class or -chá-class attestations about the speaker's own state, because all three produce the same surface form. The grammar move at the protocol level is one way to escape the impossibility — not by solving the verification problem, but by forcing the class to be declared, after which the question becomes "do we trust the declaration" rather than "can we infer the class."
- **The layered ontology strawman** treats binding moments as first-class objects with provenance. The evidential grammar adds a typology to that provenance — not just *who* signed *when*, but with *what kind* of epistemic warrant. The ser layer of the strawman's haber/ser/estar architecture would naturally carry evidential class on each binding moment.
- **Brandom's inferentialism** treats meaning as constituted by the inferential moves a term licenses. The evidential class of an attestation constrains what inferences downstream consumers may make — a -chá attestation does not license the same inferences a -mi attestation does. The grammar formalizes this distinction.

## 6. Status of This Note

This is speculation, not a research strawman. The bet might not work. Specifically: the operational overhead of enforcing evidential class at the protocol level may exceed its audit value; the three-class typology may be insufficient or excessive for the domain; the composed-evidentials problem may make the whole scheme intractable in practice; the constative/performative trap may require a more general framework that subsumes evidentiality as a special case. Each of these is a real open question, not a rhetorical concern.

The note exists because the morning's conversation produced this thread and the strawman discipline correctly excluded it from the foundation document. Producing it separately, with explicitly different epistemic status from the strawman, honors both the discipline and the productive impulse the thread represents. It is the kind of artifact the layered ontology research line will produce many of — speculative side-notes that may or may not graduate into strawmen, and may or may not survive contact with concrete substrate, but are worth documenting because the moves they make are not obvious and won't be recoverable from the strawman alone.

The most interesting move in this note, structurally, is probably the self-reflexive one in §3 — that the audit of an attestation system applies the same evidential grammar recursively to the system itself. If that move holds, it suggests evidentiality is not just a feature of the attestation layer but a property the attestation layer must have *about itself* to be auditable in any deep sense. That is the thread most worth following if any of this graduates.

---

*This exploratory note is companion to the layered ontology strawman dated 2026-05-13. It deliberately does not commit to a proposal. If the most interesting thread (the self-reflexive recursion in §3) survives further attention, the proposal version would be a separate document.*
