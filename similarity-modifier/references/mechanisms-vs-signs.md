# Mechanisms vs Signs

The central discipline of this modifier skill. Most casual similarity-reporting collapses these two; keeping them separate is most of what makes the analysis useful.

## The distinction

A **sign** is *what you can observe*: the shared word, the matching distribution, the parallel structure, the overlapping cluster. Signs are external and (often) measurable. Two careful readers should largely agree on whether a sign is present.

A **mechanism** is *the generative process that produced the sign*: why is this resemblance here? Mechanisms are inferred, not observed. Different mechanisms can produce the same sign. The same mechanism can produce different signs in different cases.

The relationship is many-to-many. A given mechanism (say, direct influence) might produce: lexical reuse, structural parallels, argumentative echoes, or none of these visibly. A given sign (say, a shared rare phrase) might come from: direct influence, a shared third source, convergent coinage, or stunning coincidence. The job is to find which mechanism *best explains the pattern of signs* you have — not any single sign in isolation.

## The mechanism catalogue

### Shared origin / common source
Both items derive from a common antecedent that neither is, but both reflect. Two translations of the same original. Two papers citing the same passage. Two datasets drawn from the same population. The shared source is upstream of both items.

### Direct influence / derivation
One item is causally downstream of the other. A revised draft. A quotation. A reply that incorporates language from the message it replies to. The causal arrow points from one item to the other.

### Convergence
Independent paths arriving at the same form because shared constraints, problems, or environments narrow the solution space. Two writers facing the same rhetorical problem may independently land on a similar structure. Two species facing the same selective pressure evolve similar morphology. No causal link between the items, but a shared constraint operating on both.

### Common cause
A third factor causes both items to look the way they do, independently. Two datasets show the same pattern because they're both responding to the same underlying real-world phenomenon, with no causal link between the datasets themselves. Distinct from shared-origin: the third factor isn't an antecedent the items derive from, it's a current cause acting on both.

### Selection effect
The similarity is real, but it's an artifact of how the items were chosen for comparison. If you only consider cases where A and B match, you make matching look more frequent than it is in the wild. Common in retrospective analyses.

### Leakage / contamination
The two items aren't really independent. Some of the content of one is materially present in the other (training-set bleed, sample overlap, copy-paste in a workflow, a shared review pass). Distinct from direct-influence by being usually inadvertent and usually undisclosed.

### Measurement artifact
The similarity exists in the measurement, not in the world. Two surveys "agree" because both used a leading question that pushed respondents in the same direction. Two clustering analyses pick out the same structure because both used the same noisy feature scaling. The signs are real but they're telling you about the instrument, not the thing being measured.

### Period / genre / convention
Both items reflect the conventions of a time, place, genre, or community. Two academic papers from 1995 share features that 1995-papers share; that's not influence, that's the era. The mechanism here is sociological — the items are similar because they were produced by participants in the same shared practice.

### Chance / coincidence
The signs are real but produced by no particular mechanism worth naming. Default to this only when the joint probability of the signs under a null model is non-trivial. For rare-feature matches, chance is usually a *weak* explanation, not a strong one. Be especially wary of using "coincidence" as a catch-all when you haven't seriously considered the others — it tends to be the explanation we reach for when we've stopped looking.

## Reasoning about which mechanism is most likely

A few useful moves:

**Compare against a null.** What would the signs look like if no special mechanism were operating — just the base rate of agreement between any two random items from this population? Strong signs are strong because they're unlikely under the null. If the null already predicts what you're seeing, no mechanism needs to be invoked.

**Look for joint patterns.** A single sign is hard to attribute. A *pattern* of signs across multiple dimensions narrows the field substantially. Multiple rare matches in lexical, structural, and argumentative dimensions simultaneously is much harder to explain by convergence or chance than any single one of them would be.

**Find a discriminating prediction.** Different mechanisms imply different *additional* signs. Direct influence predicts traces in the order of presentation, the specific examples chosen, the idiosyncrasies of one author appearing in the other. Convergence predicts independence in these incidentals even where the load-bearing structure matches. When mechanisms are competing, look for the signs that would distinguish them — and check whether those signs are present.

**Weight the prior.** Is the mechanism plausible *given the world*? Did these items exist in places where one author could have seen the other? Were these datasets collected by overlapping teams? Mechanisms that are physically impossible in context should be ruled out before they're considered. A prior of zero forecloses inference no matter how good the evidence.

**Use the most parsimonious account that fits.** When several mechanisms are compatible with the signs, prefer the one that requires the fewest additional assumptions. But "parsimony" isn't a license to default to "chance" — chance is rarely the parsimonious explanation for rare-feature patterns.

**Stay honest about undetermined cases.** If two mechanisms are roughly equally supported, say so. "Signs are strong; mechanism is undetermined between shared-origin and direct-influence; resolving would require [X]" is a better finding than picking one for the sake of confidence. The job isn't always to name a mechanism — sometimes the job is to characterise the inferential situation accurately.

## Tags

In output, use:

- `#shared-origin`
- `#direct-influence`
- `#convergent`
- `#common-cause`
- `#selection`
- `#leakage`
- `#artifact`
- `#period-genre`
- `#chance`
- `#mechanism-undetermined` — when you've considered the options and the evidence doesn't pick one out

Multiple mechanism tags can appear on a single finding when several are plausible candidates. The narrative should then explain which is preferred and why, or note the ambiguity if no preference is warranted.
