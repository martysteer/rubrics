---
name: similarity-modifier
description: A modifier skill — not a standalone skill, and does not run alone. Load this alongside another (primary) skill; this then equips that primary skill to detect, assess, measure, and report on similarity and association. It bootstraps a context-appropriate similarity rubric — naming the relevant types and categories of similarity for the situation, separating *mechanisms* (the why) from *signs* (the observable evidence), and tagging findings with a small taxonomy. Use this whenever the user wants to compare items, identify similarities, trace echoes/derivations/correspondences, detect plagiarism or influence, deduplicate or compare datasets, find analogies, or explain why two things look alike — across text, prose, ideas, datasets, or results. Especially valuable when the question is not just "are these similar?" but "in what specific ways, by what mechanism, in what context, and with what evidence?" If loaded without a primary skill doing substantive work, this skill should remain inert — it has no deliverable of its own. See `references/modifier-pattern.md` for the general modifier-skill pattern this follows.
---

# Rubric-Bootstrap Skill

> ⚙️ **Modifier skill — not a standalone skill.**
>
> This skill has no task of its own and produces no deliverable on its own. It works by changing how a separately-loaded *primary* skill detects, frames, measures, and reports on similarity and association. Load it **alongside** a primary skill that is doing the substantive work. If no primary skill is active, this skill should remain inert and wait — it is not a task skill in disguise, and it should not try to act like one.
>
> For the general pattern this skill follows (and how it differs from ordinary task skills), see `references/modifier-pattern.md`.

## What this is, and what makes it a *modifier* skill

This is a **modifier skill** — sometimes called a *cross-cutting* or *augmenting* skill. Modifier skills are distinct from ordinary task skills in three important ways:

1. **No task of their own.** An ordinary skill handles a specific kind of task end-to-end — creating a Word document, extracting data from a PDF, building a presentation. A modifier skill has no such task. It exists only to *change how some other task is done* when a particular cross-cutting concern (here: similarity and association) becomes relevant inside that task.

2. **No standalone deliverable.** An ordinary skill produces something — a file, a report, a piece of code. A modifier skill produces nothing on its own; if loaded alone, it should remain inert and wait. Its "output" is a different shape of output coming from a primary skill that is also loaded.

3. **Compose, don't replace.** Modifier skills are designed to *stack* with primary skills, not to compete with them. Loading this skill alongside `writing-analysis` doesn't replace writing-analysis with similarity-reporting; it teaches writing-analysis to handle similarity-reporting *better* when it comes up inside writing-analysis's normal work.

If you find yourself describing a task this skill handles end-to-end, something has gone wrong: either the task is actually being handled by a primary skill (and this is doing modifier work on top, which is fine), or this skill is being misused as a task skill (which is not fine — the deliverable will be thin and free-floating).

### How loading works in practice

The user explicitly loads two skills together: this modifier and a primary skill. The primary skill handles the substantive task. Whenever a similarity or association sub-task arises inside that work, the primary skill switches into the discipline laid out below — separating signs from mechanisms, selecting 3–7 dimensions from the taxonomy, producing the three-layer output format (tags, table, narrative).

If the user's task doesn't involve similarity in any meaningful way — a simple lookup, a generation task, a refactor — this skill stays out of the way. Don't manufacture similarity questions where there aren't any. The discipline below earns its overhead only when there is real comparative work to do.

### Telling whether the skill is misfiring

The skill is probably being misused if:

- It's loaded with no primary skill, and the model is trying to do a substantive task using it alone. *The modifier has no task; the work will be thin or vacuous.*
- The primary skill's task isn't comparative or associative in any meaningful sense, and the three-layer output format is being forced onto it anyway. *Let the primary do its work; the modifier should be inert.*
- Every category in the taxonomy is being applied reflexively, regardless of relevance. *The bootstrap step is supposed to* select *; selection is what makes this a rubric rather than a checklist.*
- The output reports signs without candidate mechanisms, or asserts mechanisms without grounding in signs. *The core discipline isn't being followed — only its surface tags are.*

When any of these happen, the fix is usually to step back to the bootstrap process below and restart from step 1.

## The two-pillar discipline: signs vs mechanisms

Reporting on similarity usually collapses two distinct things. Keeping them separate is most of what this skill is for.

- **Signs** — the *observable evidence* of resemblance. Shared words, overlapping distributions, matching structures, co-occurring features, equivalent shapes, paralleling rhythms. Signs are what you can point to and (often) measure.
- **Mechanisms** — the *generative reason* the signs are there. Shared origin, direct influence, convergent process (different paths reaching the same form under shared constraints), common cause, selection effect, measurement artifact, or pure coincidence. Mechanisms are why.

A similarity report that lists signs without naming a candidate mechanism is incomplete: it tells the reader *what* but not *why*. A report that asserts a mechanism without grounding it in signs is speculation. Always carry both.

When the mechanism is genuinely undetermined from the available evidence, **say so explicitly**. "Signs strongly present; mechanism undetermined between shared-origin and direct-influence" is a more honest finding than a confident guess. Be especially careful not to default to "coincidence" — it is almost always the least informative mechanism on offer and rarely the most likely.

See `references/mechanisms-vs-signs.md` for the full mechanism catalogue and reasoning patterns.

## Bootstrapping the rubric (the core process)

The rubric isn't a fixed template. When this skill is active, the primary skill should build the rubric *for the specific situation* using these steps:

1. **Articulate the comparison.** What two (or more) things are being assessed for similarity? State them precisely. Vague targets produce vague rubrics. "Two paragraphs from Author A vs Author B's 1987 essay" is a usable target; "their writing styles" is not yet.

2. **Identify the domain.** Text/prose/ideas, or data/datasets/results, or a mix. This selects which catalogue of similarity types is in play.

3. **Identify the use-context.** Why does the similarity question matter — attribution, deduplication, analogy-finding, lineage tracing, leakage detection, anomaly recognition, model evaluation, comparative argument? The use-context determines which categories of similarity carry information and which are noise. See `references/contexts.md`.

4. **Select 3–7 rubric dimensions.** From the taxonomy in `references/similarity-taxonomy.md`, choose the categories most relevant to this comparison and use-context. **Do not apply every category in the taxonomy.** Irrelevant dimensions dilute the analysis and bury the real signal. Three to seven is the right range — fewer and you may miss something material, more and the rubric stops being a rubric.

5. **For each selected dimension, gather signs and consider mechanisms.** Be specific about signs (quote, cite, measure). Then enumerate the candidate mechanisms that could plausibly have produced those signs, and weigh them.

6. **Assemble into the output format below.** Don't just report findings — tag and structure them.

Step 4 is the actual "bootstrap": the rubric is constructed for this situation, not handed down. The skill's value comes from being selective and contextual, not from applying a fixed checklist.

## Domain guidance (short)

**Text/prose & ideas.** Useful similarity categories typically include lexical/surface, syntactic/structural, semantic, pragmatic (function/intent), stylistic/register, thematic, argumentative (claims and reasoning shape), genealogical (derivation/influence), and analogical (relational mapping, A:B :: C:D). Mechanisms commonly in play: direct influence, shared source, convergent solution to a writing problem, period/genre conventions, coincidental phrasing.

**Data/datasets/results.** Useful similarity categories typically include schematic (columns, types, codings), distributional (shape, moments, tails), correlational (dependence structure), magnitude/scale, temporal (co-occurrence, lag, periodicity), cluster/grouping, predictive substitutability (do they behave the same under downstream models?), and causal-structural (when the generative process is known or inferable). Mechanisms commonly in play: shared generative process, sampling from the same population, leakage/contamination, confounding by a third variable, measurement-artifact alignment, coincidence.

For the full catalogue with definitions and examples, see `references/similarity-taxonomy.md`.

## Output format

Every similarity finding produced by the primary skill (with this skill loaded) should carry three layers.

### Layer 1 — Tagged taxonomy (inline)

Each observed similarity is tagged inline using this micro-vocabulary:

- **Type tag** (what kind of similarity): `#semantic`, `#structural`, `#distributional`, `#stylistic`, `#thematic`, `#analogical`, `#schematic`, `#temporal`, `#correlational`, `#argumentative`, `#genealogical`, `#lexical`, `#pragmatic`, `#causal-structural`, `#predictive-substitutability`, or another from the taxonomy.
- **Mechanism tag** (candidate why): `#shared-origin`, `#direct-influence`, `#convergent`, `#common-cause`, `#selection`, `#leakage`, `#artifact`, `#period-genre`, `#chance`, or `#mechanism-undetermined`.
- **Strength**: `[low]`, `[moderate]`, `[strong]`. Strength describes the signs, not the mechanism. A strong sign can still have an unknown mechanism.

Example inline finding: *Both passages open with a rhetorical question followed by a one-word answer.* `#structural #stylistic #convergent [moderate]`

### Layer 2 — Rubric scaffold (table)

A compact table summarising the selected dimensions:

| Dimension | Signs (what's observed) | Candidate mechanism(s) | Strength | Relevance to use-context |
| --- | --- | --- | --- | --- |
| ... | ... | ... | ... | ... |

Keep cells concise. The table is a scaffold, not the full argument — the narrative carries the argument.

### Layer 3 — Narrative explanation (prose)

A short prose section (typically 2–6 paragraphs) that:

- Walks the reader through the most important signs and their candidate mechanisms.
- Distinguishes findings the evidence actually supports from findings that are plausible but not established.
- States explicitly where mechanism is undetermined.
- Connects the findings back to the use-context — why these similarities matter for the task at hand.

The narrative is where you handle the things a table can't: weighing competing mechanisms, noting counterexamples, flagging cases where surface similarity hides deep difference (or vice versa).

## A few patterns worth knowing

**Surface vs deep.** Two things can share many surface features but differ in the relational/causal structure underneath, or share underlying structure while looking superficially different. When this distinction matters, name it explicitly in the narrative — it changes what the similarity is *evidence of*.

**Necessary vs incidental signs.** A sign is *necessary* if any reasonable instance of the underlying mechanism would produce it; *incidental* if it's just one of many possible expressions. Necessary signs carry more inferential weight than incidental ones. The tags don't track this directly — flag it in the narrative when load-bearing.

**Rare shared features.** Two items sharing a *common* feature is weak evidence (lots of things share it). Two items sharing a *rare* feature is strong evidence. When grading strength, weight by rarity, not by count. Five rare matches > fifty common ones.

**Direction.** Similarity is often treated as symmetric ("A is similar to B" = "B is similar to A"), but for influence and derivation it isn't. Mark direction in the narrative when it's known or estimable. Chronology, drafts, and external evidence help.

**Robustness.** A similarity that holds across perturbations (paraphrase, resampling, recoding, translation, choice of metric) is more trustworthy than one that's fragile to small changes. Note robustness where you have it.

## Worked examples

### Example 1 — Two short essays

*Primary skill: writing-analysis. User asks: "Are these two essays similar enough that one might have been influenced by the other?"*

- **Articulate**: Essay A (1962), Essay B (1989), same topic, different authors.
- **Domain**: text/ideas.
- **Use-context**: influence/attribution.
- **Selected dimensions**: semantic, argumentative, structural, lexical, thematic. (Skipping distributional and schematic — not applicable.)
- **Findings (illustrative)**:
  - Same three-part argument structure. `#argumentative #convergent [moderate]`
  - One unusual metaphor reused with slight variation. `#lexical #direct-influence [strong]` — rare phrase, low base rate.
  - Thematic overlap on a then-popular topic. `#thematic #common-cause [low]` — both writing in a moment where this topic was widely discussed.
- **Narrative** names the metaphor reuse as the load-bearing finding, notes argumentative parallels are likely convergent (a natural shape for that kind of argument), and concludes the influence hypothesis is plausible but rests primarily on one rare-feature match — which would be worth checking against other essays by Author A from the same period.

### Example 2 — Two datasets

*Primary skill: data-analysis. User asks: "These two survey datasets are supposed to be from different populations — but the results look suspiciously alike. Are they?"*

- **Articulate**: Dataset A (n=2,400, source X), Dataset B (n=1,800, source Y), both 2023.
- **Domain**: data/results.
- **Use-context**: leakage / contamination detection.
- **Selected dimensions**: schematic, distributional, correlational, predictive substitutability. (Skipping temporal — single snapshot. Skipping cluster — not the question.)
- **Findings (illustrative)**:
  - Identical column schema with same exact answer-choice text. `#schematic #shared-origin [strong]` — could be common instrument.
  - Distributions match within sampling noise on 7 of 10 variables. `#distributional #shared-origin` or `#leakage [strong]`.
  - Correlation matrices align to r=0.94 across paired cells. `#correlational [strong]`.
  - A model trained on A predicts B nearly as well as on held-out A. `#predictive-substitutability #leakage [strong]`.
- **Narrative** argues the joint pattern — especially predictive substitutability — is hard to explain by "different populations measured with the same instrument" and more parsimoniously explained by overlap or contamination between the two samples. Flags the alternative (genuinely identical populations producing identical patterns) as possible but unlikely given that the use-context is precisely "are these supposed to be different?"

## Reference files

- `references/modifier-pattern.md` — the general modifier-skill pattern this skill follows, including how modifier skills differ from task skills, how they compose with primary skills, and how to tell when one is misfiring. Read this if the modifier framing is unfamiliar.
- `references/similarity-taxonomy.md` — the full catalogue of similarity types organised by domain, with definitions and examples. Read when bootstrapping to select dimensions.
- `references/mechanisms-vs-signs.md` — extended treatment of the central distinction, the mechanism catalogue, and how to reason about which mechanisms are plausible. Read when weighing candidate mechanisms.
- `references/contexts.md` — common use-contexts (attribution, deduplication, analogy, leakage detection, etc.) with notes on which similarity dimensions tend to be informative in each. Read at step 3 of bootstrapping.

You don't need all of these for every task. Read the ones relevant to the comparison at hand.

## When this skill should stay inert

If the user's question genuinely doesn't involve similarity or association — simple lookup, generation, refactor, unrelated transformation — this skill should stay out of the way. Don't manufacture similarity questions where none exist, and don't impose the three-layer output format on tasks that wouldn't benefit from it. As a modifier skill, staying inert when the cross-cutting concern isn't active is not a failure mode — it's the correct behaviour. The point is to upgrade similarity-reporting *where it's already happening*, not to make every task a comparative one.
