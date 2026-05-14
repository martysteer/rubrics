# The Modifier-Skill Pattern

The general pattern this skill follows, written for someone trying to understand what makes a "modifier skill" distinct from an ordinary skill — and how to use, design, or extend them.

## What modifier skills are

Most skills are *task skills*: they handle a specific kind of task end-to-end. Create a Word document. Build a chart. Extract data from a PDF. The user loads such a skill, gives it a task, and gets a deliverable back.

A **modifier skill** is different. It does not handle a task; it changes how *other* skills handle their tasks. Specifically, it installs a discipline, a vocabulary, a rubric, or an output format that the primary skill then uses whenever a particular cross-cutting concern arises inside the primary's work.

Think of task skills as verbs ("create", "extract", "build") and modifier skills as adverbs or adjectives that qualify the verb without replacing it.

The modifier skill in this folder is one instance of the pattern, specialised to similarity and association. Other modifier skills could handle uncertainty-quantification, ethical-considerations-flagging, source-quality-grading, audit-trail-emission, or any other cross-cutting concern. The mechanics are the same — only the substantive content of the discipline differs.

## Why the pattern exists

Some concerns cut across many kinds of tasks. Reporting on similarity, for instance, can come up inside writing analysis, inside data analysis, inside historiographic work, inside model evaluation, inside qualitative research. Building the similarity discipline into every one of those primary skills would mean duplicating it many times — with inevitable drift between copies and inevitable inconsistency in how the concern gets handled.

Better: factor the cross-cutting concern into a modifier skill that any of those primary skills can compose with. The primary skills stay focused on their own substantive work; the modifier carries the cross-cutting discipline; the user (or another harness) decides when to apply it.

This is the same separation-of-concerns logic that motivates aspect-oriented programming, middleware, or mixin classes in software design. It's a structural move, and it pays off the same way structural moves usually pay off — fewer copies, fewer drift bugs, easier evolution.

## How modifier skills compose with primaries

Two skills loaded simultaneously, with distinct roles:

- **Primary skill** — has the task. Owns the work. Produces the deliverable. Sets the overall shape of the output.
- **Modifier skill** — has no task. Owns a sub-concern that may or may not arise inside the primary's work. When the sub-concern arises, the modifier dictates how to handle it; otherwise, the modifier stays inert.

The model holding both skills in context should read both, register which is the primary (it has the active task), register which is the modifier (it has no task but offers a discipline), and apply the modifier's discipline only when the relevant sub-concern actually arises inside the primary's work.

A modifier that always activates is a tax on every primary skill it gets paired with. A modifier that never activates is dead weight. A well-designed modifier activates *exactly when its sub-concern is in play* — no more, no less.

## Properties a well-designed modifier skill has

1. **No standalone task.** If you can describe a complete task the modifier handles end-to-end, it isn't really a modifier — it's a task skill in disguise. Try to factor it again, or accept that it's a task skill and rewrite accordingly.

2. **Explicit about what it modifies.** The modifier should clearly name the kind of sub-task it engages with (here: similarity-and-association reporting). Vague modifiers either don't trigger when they should, or intrude when they shouldn't — both fail modes that come from underspecifying the trigger.

3. **Inert by default.** When the relevant sub-concern isn't present, the modifier should stay out of the way. This isn't a failure state; it's the correct behaviour. Modifiers that always activate end up degrading every primary they're paired with.

4. **Composable with arbitrary primaries.** A good modifier doesn't assume a specific primary skill. It says "whenever similarity-reporting happens, do X" — and works whether the surrounding work is writing analysis, data analysis, anomaly detection, or anything else. If a modifier only composes well with one specific primary, it should probably be merged into that primary.

5. **Output integrates rather than competes.** The modifier should shape the primary skill's output — adding structure, tags, sub-sections, an additional pass — rather than producing a parallel output stream that fights with the primary's deliverable. Two parallel outputs confuse the user.

## How to invoke

The intended invocation pattern is: the user loads both skills explicitly, side by side, in the same session. The model then holds both descriptions in context and integrates accordingly.

Other invocation patterns are possible:

- **Calling skills referencing modifiers from their own SKILL.md** — a primary skill could say "for similarity reporting, see modifier X" and let the model load on demand. Useful but creates implicit dependencies between skills.
- **Harness-auto-loaded modifiers** — a runtime could detect that the current task involves similarity reporting and auto-load this modifier. Useful but takes the decision out of the user's hands.

This skill is written for the explicit-co-load case, which keeps the composition decision with the user and avoids surprise.

## How to tell a modifier is misfiring

- The model produces this modifier's output format on a task that wasn't actually comparative or associative. *The modifier should have stayed inert; instead it activated reflexively on a keyword match.*
- The model tries to use the modifier alone, with no primary skill, and ends up producing a free-floating discussion with no actual content to analyse. *The modifier needs a primary; without one, it has nothing to modify.*
- The model applies every category in the modifier's taxonomy by default, rather than selecting a relevant subset. *The bootstrap or selection step in the modifier isn't being followed; the rubric becomes a checklist.*
- The model adopts the modifier's surface vocabulary (tags, table headers, named sections) without adopting the underlying discipline (the actual analytic moves the modifier is asking for). *The form is in place but the substance is missing — a common and easy-to-miss failure mode.*

When you see any of these, the fix usually isn't a tweak to the modifier — it's restarting from the modifier's bootstrap or trigger step and being more deliberate about whether to activate.

## A note on naming

Modifier skills are sometimes named for what they *contain* (e.g., a similarity rubric), sometimes for what they *do to other skills* (e.g., "augments with X"), and sometimes for the *pattern* itself (e.g., "X-modifier"). All three conventions work; the important thing is that the name plus description make the modifier nature obvious at a glance, so a model loading the skill doesn't mistake it for a task skill.
