# ReasonTouch Completion Blueprint
## Chapter 5 — The Continue Path

Version 1.0 (Draft)

---

# 1. Introduction

The **Continue Path** is the first reasoning pathway that will be completed end-to-end.

This decision is deliberate.

Rather than attempting to complete every suggestion type simultaneously, Version 1 will establish one fully realised reasoning pipeline that serves as the architectural template for every future pathway.

The Continue Path therefore becomes more than simply a feature.

It becomes the reference implementation for the entire planning architecture.

Once complete, the remaining pathways—Resolve, Build Tension, Surprise Me, Modulate, and others—can be constructed by replacing only the planning strategy while preserving the remainder of the pipeline.

---

# 2. The User's Expectation

When a musician presses **Continue**, they are rarely asking:

> "Give me another chord."

Instead, they are asking something far more sophisticated.

Typical intentions include:

- Continue this musical idea.
- Keep the same style.
- Preserve the mood.
- Develop the phrase naturally.
- Avoid repeating myself.
- Don't surprise me unnecessarily.

This distinction is critical.

The Continue Path is therefore not a chord generator.

It is a **musical continuation planner**.

---

# 3. Design Philosophy

The Continue Path follows one central rule:

> Every continuation should feel inevitable in hindsight.

The user should experience the result as though the music naturally wanted to continue in that direction.

This differs fundamentally from random progression generation.

The planner should favour:

- coherence
- momentum
- stylistic consistency
- harmonic logic
- musical direction

rather than novelty for its own sake.

---

# 4. High-Level Workflow

The completed Continue pipeline is expected to operate as follows.

```
User presses Continue

↓

Acquire Current Progression

↓

Analyse Progression

↓

Create ProgressionAnalysis

↓

Pass Analysis to Pairing Engine

↓

Determine Relationship

↓

Select Continue Strategy

↓

Generate Candidate Phrases

↓

Evaluate Candidates

↓

Rank Results

↓

Generate Explanations

↓

Display Suggestions
```

Every stage has a clearly defined responsibility.

No stage duplicates the work of another.

---

# 5. Stage One — Context Acquisition

The planner begins by gathering the current musical state.

Required information includes:

- progression
- key
- detected tonic
- phrase length
- mood bias
- active workspace
- user preferences
- confidence values

This stage performs no reasoning.

It merely establishes context.

---

# 6. Stage Two — Harmonic Analysis

The existing analysis infrastructure is then invoked.

Rather than recalculating information later, the Continue Path immediately creates a comprehensive `ProgressionAnalysis`.

Typical outputs include:

```
Key

C Major

Cadence

Half Cadence

Stability

0.42

Energy

0.68

Ending Function

Dominant

Confidence

0.91
```

Every later decision is based upon this object.

---

# 7. Stage Three — Pairing Analysis

Instead of generating chords immediately, the planner asks the Pairing Engine:

> "What kind of phrase should follow this one?"

Typical responses include:

```
Continue

Open Continuation

Confidence 0.93
```

or

```
Continue

Develop Existing Motif

Confidence 0.88
```

The planner therefore understands **where** the music should go before deciding **how** to get there.

---

# 8. Stage Four — Strategy Selection

Once the desired relationship has been identified, the Continue Strategy becomes active.

Its responsibility is narrowly defined.

Given:

- analysis
- destination
- planning constraints

produce several musically convincing continuation plans.

It does **not** concern itself with user interface or presentation.

---

# 9. Candidate Generation

Rather than producing one answer, the planner should generate several candidate phrases.

For example:

Candidate A

```
vi → ii → V → I
```

Candidate B

```
IV → V → I → vi
```

Candidate C

```
ii → V7 → iii → vi
```

Candidate D

```
I → IV → ii → V
```

These candidates are still provisional.

Evaluation occurs next.

---

# 10. Evaluation Criteria

Each candidate should be scored independently.

Suggested criteria include:

## Harmonic Correctness

Does every chord function appropriately?

---

## Functional Flow

Do harmonic functions progress naturally?

---

## Voice Leading

Can chord transitions be played smoothly?

---

## Stylistic Consistency

Does the continuation match the established style?

---

## Energy Curve

Does musical energy evolve appropriately?

---

## Phrase Balance

Does the continuation feel proportionate to the opening phrase?

---

## Novelty

Avoid excessive repetition without introducing unnecessary instability.

---

## Confidence

Overall confidence should become a weighted combination of all evaluation criteria.

---

# 11. Ranking

Candidates are ranked rather than filtered.

Example:

| Rank | Score | Purpose |
|------|------:|---------|
| 1 | 0.95 | Continue Naturally |
| 2 | 0.90 | Slight Variation |
| 3 | 0.86 | Extended Continuation |
| 4 | 0.81 | More Adventurous |

These rankings map directly onto the four suggestion cards already present within the interface.

---

# 12. Explanation Generation

Each continuation should include a human-readable explanation.

Examples include:

> Continues the predominant-to-dominant movement established in the opening phrase.

---

> Preserves the current energy while delaying final resolution.

---

> Repeats the established harmonic rhythm before introducing variation.

---

> Maintains tonic focus while extending phrase length.

These explanations reinforce the educational philosophy of ReasonTouch.

---

# 13. User Presentation

The UI should never display raw chord lists alone.

Instead each suggestion becomes a complete musical recommendation.

Example:

```
Continue Naturally

Am → Dm → G → C

Confidence

95%

Reason

Completes the expected
predominant–dominant–tonic cycle.
```

This is considerably richer than merely listing four possible chords.

---

# 14. Reusing Existing Components

One of the audit's most significant findings was that much of the Continue Path already exists in fragmented form.

Existing components include:

- KeyDetector
- ChordSuggestionEngine
- ProgressionAnalysis
- ContinueStrategy
- GeneratedProgression
- explanation models
- confidence calculations

The task is therefore not to invent new systems.

It is to integrate existing ones into a coherent pipeline.

---

# 15. Proposed Refactoring

The current implementation contains continuation logic distributed across multiple locations.

Examples include:

- ViewModel helper methods

- ContinueStrategy

- ChordSuggestionEngine

- UI suggestion builders

This should gradually become:

```
ContinuePlanner

↓

Pairing Engine

↓

Continue Strategy

↓

Candidate Evaluator

↓

Explanation Builder

↓

UI
```

The ViewModel should orchestrate the process rather than implement musical reasoning itself.

---

# 16. Success Criteria

The Continue Path can be considered complete when it satisfies the following conditions.

✔ Uses `ProgressionAnalysis` as its sole analytical input.

✔ Consults the Pairing Engine before generating phrases.

✔ Produces multiple candidate continuations.

✔ Evaluates and ranks candidates.

✔ Generates meaningful musical explanations.

✔ Supplies confidence values.

✔ Remains independent of presentation logic.

✔ Requires no duplicated harmonic analysis.

---

# 17. Benefits

Completing the Continue Path first delivers several advantages.

It validates the new architecture.

It exposes weaknesses before additional pathways are implemented.

It creates reusable planning infrastructure.

It simplifies future development.

Most importantly, it provides a complete vertical slice through the reasoning engine—from user interaction to musical explanation.

Every subsequent pathway will inherit this architecture.

---

# 18. Relationship to Future Pathways

Once the Continue Path is complete, other pathways become comparatively straightforward.

For example:

```
Continue

↓

ContinueStrategy
```

becomes

```
Resolve

↓

ResolveStrategy
```

or

```
Build Tension

↓

TensionStrategy
```

The surrounding architecture remains unchanged.

Only the planning strategy differs.

This is precisely the modularity envisioned during the architectural audit.

---

# 19. Long-Term Vision

Although the Continue Path serves Version 1, its architecture anticipates future capabilities.

Potential enhancements include:

- adaptive continuation based on playing style
- genre-aware continuation
- motif recognition
- melodic continuation
- rhythmic continuation
- counter-melody generation
- orchestration-aware continuation
- AI-assisted continuation

None of these require changes to the surrounding pipeline.

They simply become richer implementations of the Continue Strategy.

---

## Next Chapter

**Chapter 6 — The Resolve Path**

Having established the complete continuation pipeline, the next chapter explores the Resolve Path, whose purpose is not to extend musical ideas but to bring them to convincing harmonic closure through intelligent cadence planning, destination selection, and resolution-aware phrase generation.

---

_End of Chapter 5_
