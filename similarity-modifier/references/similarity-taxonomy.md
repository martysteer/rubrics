# Similarity Taxonomy

A catalogue of similarity types, organised by domain. Use this when bootstrapping the rubric: scan the relevant section, pick the 3–7 categories that matter for the current comparison and use-context, and ignore the rest. Applying every category is the wrong move — irrelevant rows dilute the signal.

## Table of contents

- [Text, prose, and ideas](#text-prose-and-ideas)
- [Data, datasets, and results](#data-datasets-and-results)
- [Cross-cutting axes](#cross-cutting-axes)

## Text, prose, and ideas

### Lexical / surface
Shared specific words or phrases. Strength scales sharply with rarity: shared common words ("the", "of course") are near-worthless; shared rare phrases ("hodiernal misalignments") can be near-conclusive. Useful signs include n-gram overlap, exact-match phrases, unusual collocations, and shared idiosyncratic spellings.

### Syntactic / structural
Shared sentence shape, paragraph organisation, document structure. Two pieces that both open with a question and close with a one-word answer share structure even if no specific words overlap. Distinguish micro-structure (within sentences) from macro-structure (document-level). Structural similarity is often more diagnostic of influence than lexical, because structure tends to be less consciously chosen.

### Semantic
Shared meaning, even when expressed differently. Paraphrases. Equivalent claims in different wording. Detectable through careful reading or embedding similarity. Note that semantic equivalence is a stronger claim than topic overlap — two pieces can be on the same topic while making semantically different claims about it.

### Pragmatic
Shared function or illocutionary force — what the text is *doing*. Two passages can be semantically different but pragmatically identical: both are veiled threats, both are concessions framed as concessions, both are setups for the next move. Often missed because surface and meaning dominate attention.

### Stylistic / register
Shared voice, rhythm, register, tone, sentence-length distribution, characteristic punctuation, characteristic transitions. Strong cue for authorship attribution. Stylometric methods quantify this. Style tends to be stable across topics for a given author, which makes it more diagnostic than thematic similarity.

### Thematic
Shared topic, motif, recurring subject. Weak as evidence on its own — two people can write about the same theme independently, especially if the theme is timely. Combinable with other dimensions to support a stronger claim.

### Argumentative
Shared claims and shared reasoning structure. Two essays can argue *different positions* but follow the same argumentative move-sequence (define, distinguish, attack, concede, conclude). Or they can reach the same conclusion through wholly different reasoning. Distinguish claim-similarity from reasoning-similarity.

### Genealogical
Similarity that derives from shared lineage — direct quotation, paraphrase, derivation, adaptation, translation. Distinct from convergence: genealogical similarity implies a real causal chain between the two items, not independent arrival at the same form. The mechanism is built into the category.

### Analogical
Relational similarity — A:B :: C:D. The atoms can be wholly different; what's similar is the *relations* between them. ("The atom is like the solar system" — atoms and solar systems share almost no surface features, but the orbiting-around-a-central-mass relation maps.) Analogical similarity lives in deep structure, not vocabulary or surface feel.

## Data, datasets, and results

### Schematic
Shared structure — same columns, same types, same coding conventions, same answer choices, same units. Often the cheapest similarity to check. Strong evidence of shared instrument or shared origin; doesn't on its own say anything about the *values*, just the container.

### Distributional
Same shape of distribution for a given variable — same mean, variance, skew, kurtosis, tails, modes. Quantifiable via KS, Wasserstein, KL-divergence, or simple moment comparison. Distinguish marginal distributions from joint distributions; two datasets can match on every margin and still differ wildly in their joint structure.

### Correlational
Same dependence structure between variables. Two datasets where (X,Y) correlate at the same r, and (X,Z) at the same r, and so on across the matrix, share correlational structure. Detect via correlation-matrix comparison or copula methods.

### Magnitude / scale
Same order of magnitude or same numerical scale on key variables. Very weak as a similarity signal on its own — almost everything in a domain shares its scale — but useful as a sanity-check filter, and informative when *not* present (a scale mismatch can rule out hypotheses quickly).

### Temporal
Co-occurrence in time, shared periodicity, matching lag structures, shared seasonality, shared change-points. Time-series-specific. Often the most revealing dimension for data that has a time axis, because temporal coincidence is unlikely under most null hypotheses.

### Cluster / grouping
Same groups emerge under clustering — same number of clusters, same compositions, same boundaries. Useful when comparing the *organisation* of data, not just its values. Note that cluster similarity can be artificially high or low depending on clustering algorithm and hyperparameters; check robustness.

### Predictive substitutability
A model trained on one dataset predicts the other nearly as well as it predicts held-out data from the original. A strong, single-shot signal of underlying similarity — and often a smoking-gun for leakage or contamination. The diagnostic of choice when the use-context is "are these really independent?"

### Causal-structural
Same causal graph or same generative process, when known or inferable. Stronger than correlational similarity but much harder to establish. Usually requires either interventional evidence, domain knowledge, or careful identification arguments.

## Cross-cutting axes

These aren't categories of similarity — they're axes that cut across whichever categories you've selected. Note them in the narrative when they're load-bearing.

- **Surface vs deep.** Surface features can match while deep relations differ (and vice versa). Two texts using the same words may make opposite arguments; two datasets with very different distributions may have identical causal structure.
- **Necessary vs incidental.** Some signs are inevitable expressions of the underlying mechanism; others are contingent. Necessary signs carry more inferential weight.
- **Rare vs common.** Strength scales sharply with rarity. Five rare matches beats fifty common ones.
- **Direction.** A→B, B→A, mutual, or none. Matters most for influence/derivation. Chronology, drafts, and external evidence resolve it.
- **Robustness.** Does the similarity survive paraphrase, resampling, recoding, perturbation, choice of metric? Fragile similarities are less trustworthy.
- **Granularity.** Token-level, chunk-level, whole-item. Similarity at one scale doesn't entail similarity at another — and the relevant scale depends on the use-context.
