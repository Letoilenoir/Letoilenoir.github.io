# ReasonTouch Completion Blueprint
## Chapter 11 — Section-Aware Composition Planning

**Version:** 1.0 (Blueprint Draft)

---

# 1. Purpose

Everything developed so far assumes that a progression exists as an isolated musical object.

In reality, almost no piece of music is written that way.

Every progression serves a structural purpose within a larger composition.

For example:

- an intro prepares
- a verse tells a story
- a pre-chorus builds expectation
- a chorus delivers release
- a bridge provides contrast
- an outro concludes

Exactly the same four chords may feel entirely different depending upon where they occur.

The purpose of the **Section-Aware Planner** is therefore to allow ReasonTouch to compose not merely progressions, but complete musical journeys.

---

# 2. Philosophy

The architectural audit concluded that composition operates on multiple hierarchical levels.

```
Chord

↓

Progression

↓

Phrase

↓

Section

↓

Song
```

Most software understands only the first two.

ReasonTouch aims to understand all five.

The Section Planner therefore becomes the bridge between progression generation and complete composition.

---

# 3. Position within the Architecture

The planner is inserted immediately before strategy selection.

```
Current Progression

↓

Progression Analysis

↓

Section Analysis

↓

Planning Strategy

↓

Candidate Generation

↓

Evaluation

↓

Presentation
```

Section becomes another planning input rather than another generation engine.

---

# 4. Section Identity

Each section possesses its own musical objectives.

Rather than generating "more chords", the planner asks:

> What is this section trying to achieve?

Typical section identities include:

- Intro
- Verse
- Pre-Chorus
- Chorus
- Bridge
- Solo
- Breakdown
- Outro

Each encourages different planning behaviour.

---

# 5. Intro Planning

The introduction establishes musical identity.

Typical characteristics include:

- tonal clarity
- moderate energy
- low harmonic complexity
- memorable opening gesture
- clear key centre

Example:

```
I

↓

IV

↓

I

↓

V
```

The objective is familiarity rather than surprise.

---

# 6. Verse Planning

The verse supports lyrical storytelling.

Typical properties:

- stable harmony
- repetitive patterns
- moderate movement
- room for melody
- restrained emotional range

The planner should avoid excessive harmonic distraction.

---

# 7. Pre-Chorus Planning

The pre-chorus exists to prepare the chorus.

Characteristics:

- increasing tension
- rising harmonic energy
- delayed resolution
- dominant emphasis
- growing expectation

Typical example:

```
vi

↓

IV

↓

V

↓

V
```

Notice that the tonic is intentionally delayed.

---

# 8. Chorus Planning

The chorus is usually the emotional destination.

Its objectives include:

- maximum memorability
- strong tonal centre
- emotional release
- broad harmonic clarity
- satisfying cadence

Typical example:

```
I

↓

V

↓

vi

↓

IV
```

The planner should favour recognisable, singable progressions.

---

# 9. Bridge Planning

The bridge provides contrast.

Possible techniques include:

- modulation
- modal borrowing
- chromatic movement
- altered harmony
- rhythmic variation

Unlike the chorus, the bridge is expected to surprise.

It becomes a natural consumer of the **Surprise** planning pathway developed earlier.

---

# 10. Outro Planning

The outro concludes the musical narrative.

Typical characteristics:

- increasing stability
- tonic reinforcement
- reduced harmonic activity
- authentic cadence
- emotional closure

Possible endings include:

```
IV

↓

V

↓

I
```

or

```
ii

↓

V

↓

I
```

depending upon style.

---

# 11. Section Profiles

Each section should be represented by a reusable profile.

Example:

```
SectionProfile

Name

Desired Stability

Desired Energy

Desired Tension

Cadence Preference

Phrase Length

Repetition Level

Preferred Strategies

Transition Rules
```

Like Style Profiles, these become data rather than code.

---

# 12. Interaction with Existing Strategies

Every planning strategy becomes section-aware.

---

Continue

Verse:

continue smoothly.

Bridge:

continue creatively.

Outro:

continue toward closure.

---

Resolve

Verse:

gentle resolution.

Outro:

complete resolution.

Bridge:

partial resolution only.

---

Build Tension

Intro:

low intensity.

Pre-Chorus:

maximum effectiveness.

Bridge:

controlled instability.

---

Surprise

Verse:

rare.

Bridge:

frequent.

Outro:

minimal.

---

Emotion

Hopeful Verse

≠

Hopeful Chorus

because emotional intensity differs.

---

# 13. Section Transitions

Equally important are the transitions between sections.

Examples:

```
Verse

↓

Pre-Chorus
```

requires increasing energy.

---

```
Pre-Chorus

↓

Chorus
```

requires release.

---

```
Bridge

↓

Final Chorus
```

requires renewed impact.

The planner should therefore evaluate not only each section independently, but also the quality of the transition between them.

---

# 14. Transition Objectives

Each transition can be described using measurable goals.

| Transition | Objective |
|------------|-----------|
| Intro → Verse | Establish momentum |
| Verse → Pre-Chorus | Increase expectation |
| Pre-Chorus → Chorus | Deliver release |
| Chorus → Verse | Reduce intensity |
| Verse → Bridge | Introduce contrast |
| Bridge → Chorus | Maximise impact |
| Chorus → Outro | Resolve completely |

These objectives become planning constraints.

---

# 15. Candidate Evaluation

Section-aware evaluation introduces additional criteria.

---

## Section Suitability

Does the progression fulfil the purpose of this section?

---

## Transition Quality

Does it connect naturally from the previous section?

---

## Energy Curve

Is the musical energy evolving appropriately?

---

## Emotional Continuity

Does the emotional trajectory remain coherent?

---

## Structural Balance

Does the song avoid becoming repetitive?

---

# 16. Educational Feedback

ReasonTouch should explain section-level decisions.

Examples:

> Delays tonic arrival to prepare the chorus.

---

> Introduces modal contrast suitable for a bridge.

---

> Reinforces tonic to provide a convincing ending.

---

> Repeats the harmonic loop to support lyrical focus in the verse.

These explanations teach composition rather than isolated harmony.

---

# 17. Relationship to the Workspace

The long-term vision is that each workspace understands the section currently being edited.

For example:

```
Song Workspace

↓

Verse Selected

↓

Section Planner

↓

Generation
```

Changing the selected section immediately changes planning priorities.

This makes the application feel like an intelligent compositional assistant rather than a chord generator.

---

# 18. Reusing Existing Infrastructure

The Section Planner reuses almost everything already developed.

Existing components include:

- ProgressionAnalysis
- HarmonicFunction
- Planning Strategies
- Style Profiles
- Emotion Profiles
- Pairing Engine
- Candidate Evaluation
- Confidence Scoring

The only significant addition is the SectionProfile database and transition logic.

---

# 19. Implementation Roadmap

Implementation should proceed in stages.

### Phase 1

Support:

- Intro
- Verse
- Chorus

---

### Phase 2

Add:

- Pre-Chorus
- Bridge

---

### Phase 3

Support:

- Outro
- Breakdown
- Solo

---

### Phase 4

Introduce automatic transition planning.

---

### Phase 5

Generate complete song structures.

---

### Phase 6

Support user-defined section templates.

---

# 20. Success Criteria

The Section Planner is complete when it:

- understands structural purpose
- influences every planning strategy
- supports smooth section transitions
- explains structural decisions
- reuses existing planning infrastructure
- enables generation of complete song forms

---

# 21. Architectural Significance

This chapter marks the point at which ReasonTouch evolves beyond progression generation into genuine composition planning.

The engine no longer asks merely:

> "What chord comes next?"

It begins asking:

> "What role does this music play within the composition?"

This distinction is fundamental.

It transforms the planner from a harmonic assistant into an architectural composer.

---

# 22. Looking Ahead

Once the planner understands **structure**, it becomes possible to reason about music over much longer timescales.

The next logical development is to recognise recurring musical ideas.

Themes, motifs, and harmonic fingerprints should be identified, developed, varied, and recalled throughout a composition.

This introduces the concept of **Motif and Theme Management**, allowing ReasonTouch to generate music with long-range coherence rather than isolated sections.

---

## Next Chapter

**Chapter 12 — Motif, Theme, and Long-Range Musical Memory**

This chapter introduces persistent musical memory, enabling the planning engine to recognise, develop, transform, and recall thematic material across an entire composition.

---

**End of Chapter 11**
