# Use-Contexts

Why does a similarity question matter for the task at hand? The use-context determines which similarity dimensions are informative. The same two items can be "very similar" in one use-context and "not similar enough to matter" in another.

This file lists common use-contexts with notes on which dimensions tend to be informative and which mechanisms are usually in play. Use it as a starting checklist when bootstrapping the rubric — step 3 of the process in `SKILL.md`.

## Attribution / authorship

*"Did this author write that?"*

**Most informative dimensions**: stylistic/register, lexical (especially function-word usage and characteristic phrases), syntactic, pragmatic (characteristic moves).

**Least informative**: thematic (most authors write on many themes), semantic (topics are widely shared).

**Common mechanisms in play**: direct-influence (if they did write it — a single-author causal chain), convergent (genre conventions producing apparent style match), period-genre (the era's voice rather than the author's).

## Plagiarism / derivation detection

*"Is this derived from that?"*

**Most informative**: lexical (especially rare phrases), genealogical, argumentative, structural at micro-level (passage-by-passage parallels).

**Direction matters**: A from B vs B from A. Use chronology, drafts, and external evidence.

**Common mechanisms**: direct-influence, shared-origin (both citing or paraphrasing the same earlier source — not plagiarism between them but a shared upstream), convergent (rare for substantive matches but worth ruling out).

## Influence / lineage tracing

*"Is later work influenced by earlier work?"*

**Most informative**: argumentative, conceptual, analogical (key analogies reused), genealogical, lexical (characteristic terms migrating).

**Less informative**: distributional, magnitude — irrelevant for ideas.

**Common mechanisms**: direct-influence, shared-origin (both reflecting a common earlier source), period-genre (the era spoke this way).

## Analogy finding

*"What pattern in domain A looks like a pattern in domain B?"*

**Most informative**: analogical (relational), structural, pragmatic.

**Specifically not informative**: surface lexical, surface stylistic. Analogies live in deep relations, not in vocabulary or feel. Surface dissimilarity between A and B is normal — even expected — when the analogy is real.

**Common mechanisms**: convergent (when real — same constraints producing same structures in different domains), chance (rule out via base rates), period-genre (when both domains are responding to a shared cultural or technical moment).

## Dataset deduplication / leakage detection

*"Are these two datasets actually independent?"*

**Most informative**: schematic, predictive substitutability (strongest single signal), distributional, correlational.

**Common mechanisms**: leakage, shared-origin (both from same population — legitimate or not), artifact (same instrument producing apparent agreement), chance (rule out by joint probability — usually easy to dismiss when signs are strong).

Predictive substitutability is the most diagnostic single check. If a model trained on A predicts B as well as it predicts held-out A, you've almost certainly got leakage or shared sample. Schematic identity alone is much weaker — many independent datasets use the same instrument.

## Comparative analysis (datasets)

*"How do these results compare?"*

**Most informative dimensions depend on the comparative claim being made.**
- If the claim is "different populations behave differently": distributional, correlational, magnitude.
- If the claim is "the same intervention works similarly across contexts": predictive substitutability, effect-size similarity, direction of effects.
- If the claim is "these measure the same underlying thing": correlational, causal-structural.

**Common mechanisms**: common-cause (real underlying phenomenon driving both), shared-origin (suspicious — check), artifact (same instrument inflating apparent agreement).

## Anomaly / case-based reasoning

*"Is this new case similar to a known case?"*

**Most informative**: depends on the structure of the known cases. Often pragmatic (what's this instance *doing*?), structural, argumentative, analogical.

**Common mechanisms**: convergent (similar causes produce similar cases — a useful inference), shared-origin (same source or system generating both), chance (rule out via base rates).

## Model evaluation

*"How similar are these predictions to ground truth?"*

**Most informative**: distributional (do predictions and truth share shape?), correlational (do they move together?), error structure (where do they diverge?).

**Common mechanisms**: this use-context is mostly about characterising the gap, not attributing a mechanism. But: if predictions look *too* similar to ground truth — better than the model's training data or capacity would warrant — suspect leakage.

## Cluster / typology comparison

*"Do these two groupings of items pick out the same structure?"*

**Most informative**: cluster/grouping similarity, schematic, correlational.

**Common mechanisms**: common-cause (both groupings detecting the same real structure — the optimistic case), artifact (both responding to the same nuisance variable that has nothing to do with the substantive grouping), shared-origin (the clusterings were run on overlapping inputs).

## Translation / paraphrase / rewrite quality

*"Has this preserved the original in translation or paraphrase?"*

**Most informative**: semantic (must be preserved), pragmatic (usually must be preserved), stylistic (often should be modulated — exact preservation may be a flaw), structural at macro-level.

**Less informative or actively misleading**: lexical (translation will differ lexically by design), syntactic at micro-level (will differ — different languages have different default structures).

**Common mechanisms**: direct-influence is always present (translation derives), so the question isn't *whether* one influenced the other — it's whether the influence is *faithful* on the dimensions that should be preserved.

## Default

If your use-context isn't on this list, look for the closest analogue and adapt. The general pattern is always the same: which dimensions carry information about the question I actually care about, and which are noise? Pick the informative ones, name them in the rubric, and leave the noise out.
