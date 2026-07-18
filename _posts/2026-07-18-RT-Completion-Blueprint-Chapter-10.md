# ReasonTouch Completion Blueprint
## Chapter 10 — Style-Aware Progression Planning

**Version:** 1.0 (Blueprint Draft)

---

# 1. Purpose

The previous chapter introduced **emotion as a compositional objective**.

However, identical emotions can be expressed through completely different harmonic languages depending upon musical style.

For example, the emotion *hopeful* might be realised as:

- a I–V–vi–IV progression in Pop
- a ii–V–I with extended harmony in Jazz
- a I–IV–V hymn cadence in Gospel
- a suspended pedal point in Film music
- modal harmony in Folk music

Emotion alone is therefore insufficient.

The planning engine must also understand **style**.

Style-aware planning allows ReasonTouch to produce progressions that are not merely theoretically correct, but idiomatic to the musical language being explored.

---

# 2. Philosophy

The architectural audit concluded that style should **never replace music theory**.

Instead:

```
Music Theory

↓

Style Constraints

↓

Planning

↓

Generation
```

Theory provides the rules.

Style determines which rules are most commonly used.

For example:

A tritone substitution is theoretically valid in many contexts.

It is stylistically common in Jazz.

It is stylistically rare in Country.

The planner therefore adjusts probability rather than correctness.

---

# 3. Position within the Architecture

Style becomes another layer of planning.

```
User Intent

↓

Style Selection

↓

Progression Analysis

↓

Planning Strategy

↓

Style Profile

↓

Candidate Generation

↓

Evaluation

↓

Presentation
```

This design avoids creating separate engines for every genre.

---

# 4. Style Profiles

Each musical style should be represented as a reusable profile.

Example:

```
StyleProfile

Name

Preferred Functions

Cadence Preferences

Typical Chord Colours

Borrowing Frequency

Secondary Dominant Usage

Suspension Usage

Modulation Frequency

Complexity Range

Typical Phrase Length
```

This profile becomes another planning input.

---

# 5. Example Style Definitions

---

## Pop

Characteristics

- simple harmony
- memorable progressions
- strong tonal centre
- repeated loops
- moderate tension

Typical progression:

```
I

↓

V

↓

vi

↓

IV
```

---

## Rock

Characteristics

- strong dominant movement
- modal mixture
- power chord influence
- pentatonic compatibility

Common harmony:

```
I

↓

♭VII

↓

IV

↓

I
```

---

## Jazz

Characteristics

- extended harmony
- substitutions
- ii–V chains
- altered dominants
- chromatic movement

Example:

```
ii

↓

V7

↓

Imaj7
```

---

## Blues

Characteristics

- dominant sevenths
- twelve-bar structure
- turnaround emphasis

Typical harmony:

```
I7

↓

IV7

↓

V7
```

---

## Folk

Characteristics

- modal colour
- open harmony
- gentle cadences
- strong tonic orientation

---

## Film Score

Characteristics

- chromatic mediants
- pedal harmony
- modal interchange
- suspended resolution
- emotional contour

---

# 6. Style as Probability

Rather than forbidding harmonic devices, the planner adjusts their probability.

Example:

| Device | Pop | Jazz | Film |
|---------|----:|-----:|------:|
| Secondary Dominant | Medium | Very High | High |
| Tritone Substitution | Low | Very High | Medium |
| Modal Borrowing | Medium | High | Very High |
| Chromatic Mediant | Low | Medium | Very High |
| Extended Dominants | Medium | Very High | High |

Thus:

```
Same Engine

+

Different Weights

=

Different Musical Styles
```

---

# 7. Interaction with Existing Planning Paths

Every planning strategy developed so far becomes style-aware.

---

Continue

Pop:

```
I

↓

V

↓

vi
```

Jazz:

```
ii

↓

V

↓

Imaj7
```

Film:

```
I

↓

♭VI

↓

IV
```

Same intent.

Different musical language.

---

Resolve

Pop resolves simply.

Jazz may resolve through substitutions.

Film may delay resolution.

---

Build Tension

Rock may rely upon dominant repetition.

Jazz prefers ii–V expansion.

Film often prefers chromatic ascent.

---

Surprise

Pop introduces subtle deviations.

Jazz encourages substitutions.

Film embraces unexpected mediants.

---

Emotion

Hopeful Pop

≠

Hopeful Jazz

≠

Hopeful Film

---

# 8. Candidate Generation

Candidate generation now occurs in two stages.

Stage One

Generate harmonically valid ideas.

↓

Stage Two

Filter according to style profile.

This greatly simplifies implementation.

---

# 9. Evaluation Criteria

Candidate evaluation gains several additional metrics.

---

## Style Authenticity

Would musicians recognise this as belonging to the selected style?

---

## Harmonic Validity

Does the progression remain theoretically sound?

---

## Emotional Compatibility

Does it still achieve the requested emotional objective?

---

## Musical Variety

Does it avoid clichés where appropriate?

---

## Performance Practicality

Would performers naturally play this progression within the chosen style?

---

# 10. Educational Benefits

ReasonTouch should explain stylistic decisions.

Examples:

> Uses a ii–V–I cadence typical of Jazz harmony.

---

> Introduces a borrowed ♭VII chord common in Rock.

---

> Employs modal interchange frequently found in Film scoring.

---

> Chooses open harmonic movement associated with Folk music.

These explanations transform stylistic imitation into education.

---

# 11. Future Style Library

The architecture should support an expanding catalogue of style profiles.

Examples include:

- Classical
- Romantic
- Baroque
- Jazz
- Bebop
- Fusion
- Blues
- Gospel
- Country
- Bluegrass
- Folk
- Celtic
- Pop
- Rock
- Metal
- Progressive Rock
- Funk
- Soul
- R&B
- EDM
- Ambient
- Cinematic
- Video Game
- Latin
- Flamenco
- Bossa Nova
- Reggae

Each profile simply supplies different planning preferences.

No new planning engine is required.

---

# 12. User Interaction

Style may be selected in several ways.

### Explicit

The user chooses:

> Jazz

---

### Workspace Default

Each workspace may remember a preferred style.

---

### Automatic Detection

Future versions may infer style from the existing progression.

Example:

```
ii

↓

V

↓

Imaj7
```

likely indicates Jazz.

---

# 13. Reusing Existing Infrastructure

The Style Planner requires remarkably little additional infrastructure.

Existing components include:

- ProgressionAnalysis
- HarmonicFunction
- Pairing Engine
- Planning Strategies
- Candidate Evaluation
- Confidence Scores
- GeneratedProgression

Only the StyleProfile database and weighting layer are new.

---

# 14. Implementation Roadmap

Development should proceed incrementally.

### Phase 1

Pop

Rock

Jazz

---

### Phase 2

Blues

Folk

Country

---

### Phase 3

Film

Ambient

Cinematic

---

### Phase 4

Latin

Gospel

R&B

---

### Phase 5

Automatic style detection.

---

### Phase 6

Adaptive user-defined style profiles.

---

# 15. Success Criteria

The Style-Aware Planner is complete when it:

- influences every planning pathway
- avoids duplicating planning logic
- generates idiomatic harmonic language
- explains stylistic decisions
- remains theory-driven
- allows new styles to be added through data rather than code changes

---

# 16. Architectural Significance

Style-aware planning represents one of the most important architectural milestones identified during the audit.

Rather than creating separate "Jazz Mode", "Rock Mode", or "Film Mode" generators, the system instead develops a **single intelligent planning engine** whose behaviour is shaped by reusable style profiles.

This dramatically reduces maintenance while increasing musical flexibility.

It also ensures that future planning strategies automatically inherit style awareness without requiring new implementations.

---

# 17. Looking Ahead

At this stage, ReasonTouch understands:

- harmonic structure
- cadence
- continuation
- resolution
- tension
- surprise
- emotional intent
- musical style

The next evolutionary step is to recognise **context**.

A progression does not exist in isolation.

Its role depends upon where it appears within the larger composition.

The planning engine must therefore understand concepts such as:

- verse
- chorus
- bridge
- intro
- outro
- pre-chorus
- middle eight

This introduces **section-aware composition planning**, allowing identical harmonic ideas to be interpreted differently according to their structural purpose.

---

## Next Chapter

**Chapter 11 — Section-Aware Composition Planning**

The next chapter defines how musical form becomes another planning input, enabling ReasonTouch to generate progressions that support the architecture of complete songs rather than isolated chord sequences.

---

**End of Chapter 10**
