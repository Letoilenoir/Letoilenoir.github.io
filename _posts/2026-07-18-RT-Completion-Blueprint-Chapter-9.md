# ReasonTouch Completion Blueprint
## Chapter 9 — Emotion-Driven Progression Planning

**Version:** 1.0 (Blueprint Draft)

---

# 1. Purpose

Up to this point, every planning strategy has been defined by a musical objective:

- Continue
- Resolve
- Build Tension
- Surprise Me

These represent **structural intentions**.

However, composers rarely think exclusively in structural terms.

More often they begin with an emotional goal.

Examples include:

> "I want this section to sound hopeful."

or

> "Make this darker."

or

> "Increase the drama."

or

> "This needs to feel more uplifting."

The Emotion-Driven Planning Engine exists to bridge that gap.

Rather than asking:

> "Which chord comes next?"

it asks:

> "What emotional journey should the harmony create?"

---

# 2. Philosophy

One of the discoveries made during the architectural audit was that harmony is only one contributor to musical emotion.

Emotion also emerges from:

- harmonic function
- tonal stability
- cadence behaviour
- harmonic rhythm
- register
- orchestration
- dynamics
- melody
- rhythm

ReasonTouch currently controls only part of that system.

Therefore the emotional planner should concern itself only with the dimensions under its influence.

Specifically:

- harmonic colour
- harmonic direction
- stability
- tension
- expectation
- release

This allows the planner to influence emotional perception without claiming complete control over it.

---

# 3. Position within the Architecture

Emotion becomes another planning strategy rather than a separate subsystem.

```
User Intent

↓

Emotion Target

↓

Progression Analysis

↓

Emotion Planner

↓

Candidate Generator

↓

Evaluation

↓

Ranking

↓

Presentation
```

Nothing else in the architecture changes.

---

# 4. Emotional Dimensions

Instead of treating emotions as isolated labels, the planner should represent them using several continuous dimensions.

Example:

| Dimension | Scale |
|-----------|------|
| Brightness | Dark ↔ Bright |
| Energy | Calm ↔ Energetic |
| Stability | Unresolved ↔ Stable |
| Tension | Relaxed ↔ Intense |
| Warmth | Cold ↔ Warm |
| Complexity | Simple ↔ Rich |

Every emotional target becomes a point within this multidimensional space.

---

# 5. Example Emotional Profiles

Rather than hard-coding emotions, the planner maps them onto these dimensions.

## Hopeful

```
Brightness

████████

Energy

██████

Tension

███

Stability

███████
```

---

## Melancholic

```
Brightness

██

Energy

███

Tension

████

Stability

█████
```

---

## Triumphant

```
Brightness

██████████

Energy

████████

Tension

██████

Stability

████████
```

---

## Mysterious

```
Brightness

███

Energy

████

Tension

███████

Stability

███
```

These profiles become planning targets rather than fixed chord recipes.

---

# 6. Translating Emotion into Harmony

Each emotional dimension influences harmonic decisions.

For example:

## Brightness

Influenced by:

- major tonality
- raised scale degrees
- Lydian colour
- major sixths
- add9 chords

---

## Darkness

Influenced by:

- minor tonality
- modal borrowing
- lowered sixth
- lowered seventh
- diminished colour

---

## Warmth

Influenced by:

- sixth chords
- major sevenths
- open voicings
- gentle voice leading

---

## Tension

Influenced by:

- dominant function
- altered chords
- suspensions
- chromatic movement

---

## Stability

Influenced by:

- tonic function
- authentic cadences
- root position harmony

Each planning decision therefore has measurable emotional consequences.

---

# 7. Emotional Trajectories

Emotion should evolve across time.

The planner therefore works with emotional curves rather than isolated states.

Example:

```
Calm

↓

Hopeful

↓

Excited

↓

Triumphant
```

or

```
Hopeful

↓

Uncertain

↓

Dark

↓

Resolving
```

The planner generates harmony that follows these trajectories.

---

# 8. Candidate Planning

Multiple emotional interpretations should always be produced.

Example request:

> "Make this progression more hopeful."

Possible candidates:

---

Candidate A

Increase brightness through modal interchange.

---

Candidate B

Introduce brighter substitutions while preserving cadence.

---

Candidate C

Delay dominant arrival to create optimistic expectation.

---

Candidate D

Increase consonance through smoother voice leading.

Each satisfies the same emotional request through different harmonic techniques.

---

# 9. Evaluation Criteria

Candidates should be evaluated using emotional as well as harmonic metrics.

---

## Emotional Match

Does the candidate genuinely move toward the requested emotion?

---

## Harmonic Logic

Does the progression remain musically coherent?

---

## Functional Consistency

Are borrowed chords justified?

---

## Voice Leading

Do transitions remain smooth?

---

## Structural Compatibility

Can this phrase still connect naturally to neighbouring sections?

---

# 10. Educational Feedback

ReasonTouch should explain emotional decisions.

Examples:

> Added a borrowed IV chord to soften the transition.

---

> Increased brightness by introducing Lydian colour.

---

> Reduced harmonic tension to create a calmer ending.

---

> Delayed dominant arrival to increase optimism.

The explanation helps users understand the relationship between harmony and emotion.

---

# 11. Relationship with Future Systems

The emotional planner becomes increasingly valuable as additional musical layers are introduced.

Future systems may include:

- melody generation
- bass generation
- rhythm generation
- orchestration
- articulation
- dynamics

Each subsystem can reference the same emotional profile.

For example:

```
Emotion Profile

↓

Harmony

↓

Melody

↓

Bass

↓

Rhythm

↓

Arrangement
```

This creates a unified expressive framework across the entire application.

---

# 12. Reusing Existing Infrastructure

The emotional planner reuses nearly all existing architectural components.

These include:

- ProgressionAnalysis
- HarmonicFunction
- KeyDetector
- ChordSuggestionEngine
- Progression Pairing Engine
- Candidate evaluation
- Confidence scoring

Only the planning heuristics require expansion.

---

# 13. Implementation Roadmap

Development should proceed in manageable stages.

### Phase 1

Support a small set of core emotions:

- Happy
- Sad
- Calm
- Energetic

---

### Phase 2

Introduce emotional dimensions.

---

### Phase 3

Map harmonic devices onto emotional vectors.

---

### Phase 4

Support emotional trajectories.

---

### Phase 5

Share emotional targets with melody and bass generation.

---

### Phase 6

Enable adaptive emotional planning based on user feedback and context.

---

# 14. Success Criteria

The Emotion-Driven Planner is complete when it:

- interprets emotional intent rather than chord requests
- produces multiple emotionally distinct candidates
- explains emotional decisions
- integrates with existing planning architecture
- remains harmonically coherent
- supports future expansion into melody and arrangement

---

# 15. Architectural Significance

The introduction of emotional planning marks a major evolution in ReasonTouch.

The system is no longer responding solely to harmonic objectives.

Instead, it begins to compose with **expressive intent**.

This moves the architecture closer to the way experienced composers actually think.

Rather than selecting chords first and hoping they evoke the desired feeling, the system begins with the desired feeling and derives harmonic choices that support it.

---

# 16. Looking Ahead

Emotion provides one dimension of musical intent.

The next logical step is to recognise that music also exists within stylistic conventions.

A jazz progression, a blues turnaround, a cinematic build, and a folk cadence may all express similar emotions while using entirely different harmonic languages.

The next planner therefore introduces **style-aware generation**, allowing every pathway developed so far to adapt its behaviour according to musical genre.

---

## Next Chapter

**Chapter 10 — Style-Aware Progression Planning**

This chapter defines how ReasonTouch will incorporate genre, era, and idiomatic harmonic language into the planning engine, enabling every strategy—Continue, Resolve, Build Tension, Surprise Me, and Emotion-Driven Planning—to generate results that are stylistically authentic rather than merely theoretically correct.

---

**End of Chapter 9**
