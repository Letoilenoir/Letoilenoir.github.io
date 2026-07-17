# Chapter 8 – Voice Leading and Harmonic Realisation

> *ReasonTouch Technical Companion*  
> Chapter 8

---

# 8. Voice Leading and Harmonic Realisation

## 8.1 Introduction

A progression may be theoretically perfect and yet sound awkward.

Conversely, a relatively simple progression may sound remarkably smooth if each voice moves naturally from one chord to the next.

This distinction lies at the heart of **voice leading**.

Where previous chapters described how ReasonTouch determines *which* chords should follow one another, this chapter explains how those chords will eventually be transformed into convincing musical movement.

Voice leading represents the transition from harmonic theory to musical performance.

---

# 8.2 Harmony versus Voice Leading

Harmony answers the question:

> *"Which chord should occur next?"*

Voice leading answers a different question:

> *"How should every individual note move into that next chord?"*

These are separate problems.

For example:

```
C

↓

G
```

is harmonically correct.

However, there are dozens of possible voicings.

Some require large jumps.

Others require almost no movement.

To the listener, they feel completely different.

ReasonTouch therefore treats harmonic progression and voice leading as independent architectural layers.

---

# 8.3 Architectural Position

Voice leading occurs after harmonic generation.

```
Analysis

↓

Planning

↓

Generation

↓

Voice Leading

↓

Rhythm

↓

Playback
```

By postponing voice leading until after harmonic decisions are complete, each subsystem remains focused on a single responsibility.

---

# 8.4 Why Separate the Systems?

Many composition programs combine harmony and voicing.

While simpler, this tightly couples two very different musical problems.

ReasonTouch deliberately separates them because:

- harmonic analysis becomes clearer,
- planning becomes independent of instrumentation,
- alternative voicings remain possible,
- multiple instruments can share identical harmonic plans.

One progression can therefore generate:

- piano accompaniment,
- guitar voicings,
- orchestral harmony,
- string quartet writing,

without altering the harmonic plan itself.

---

# 8.5 What Is a Voice?

A voice is an independent melodic line within a chord.

Traditional four-part writing contains:

```
Soprano

Alto

Tenor

Bass
```

Modern accompaniment may instead contain:

```
Melody

Upper harmony

Inner harmony

Bass
```

or

```
Guitar strings

Piano hands

String sections
```

The Voice-Leading Engine treats each independently while maintaining harmonic coherence.

---

# 8.6 Basic Principles

The engine aims to satisfy several classical principles.

### Minimise movement

Each note should move the shortest reasonable distance.

Example:

```
C E G

↓

C F A
```

rather than

```
C E G

↓

F A C
```

if unnecessary leaps can be avoided.

---

### Preserve common tones

Shared notes should remain where possible.

Example:

```
C Major

C E G

↓

A Minor

A C E
```

Common tones:

```
C

E
```

remain stationary while only one voice moves.

This creates smooth harmonic flow.

---

### Prefer stepwise motion

Small intervals generally sound more natural than repeated leaps.

Preferred motion:

```
C

↓

D

↓

E
```

rather than

```
C

↓

G

↓

D
```

unless stylistically justified.

---

# 8.7 Bass Movement

The bass line carries enormous structural importance.

ReasonTouch analyses:

- descending fifths
- ascending fourths
- chromatic bass
- pedal notes
- stepwise motion
- arpeggiated movement

Future versions will allow bass generation to become an independent planning subsystem.

---

# 8.8 Parallel Motion

Traditional harmony discourages excessive use of:

- parallel fifths
- parallel octaves

These weaken voice independence.

Future voice-leading evaluation may therefore penalise progressions exhibiting excessive parallel motion.

Importantly, this behaviour will remain style dependent.

Rock, jazz and orchestral writing often employ different conventions.

---

# 8.9 Chord Inversions

The harmonic planner generally works with chord identity.

Voice leading introduces inversions.

For example:

```
C

↓

G/B

↓

Am
```

instead of

```
C

↓

G

↓

Am
```

The harmony remains identical.

The bass movement becomes significantly smoother.

Future versions will automatically evaluate inversion suitability.

---

# 8.10 Register Management

Voices should occupy appropriate ranges.

Examples:

```
Bass

E1–C3
```

```
Tenor

C3–G4
```

```
Alto

G3–D5
```

```
Soprano

C4–G5
```

Maintaining realistic ranges produces more convincing arrangements.

---

# 8.11 Instrument Independence

Voice leading should not assume a particular instrument.

Instead it produces abstract note assignments.

These may later be rendered as:

- piano
- guitar
- choir
- brass
- synthesiser
- strings

Each renderer interprets the same harmonic information differently.

---

# 8.12 Guitar Considerations

Because ReasonTouch began as a guitar-focused application, guitar voice leading remains especially important.

Future guitar-specific evaluation may include:

- open-string usage
- position shifts
- barre transitions
- finger economy
- chord inversions
- ergonomic difficulty

This allows harmonically identical phrases to receive different playability scores.

---

# 8.13 Piano Considerations

Piano introduces different optimisation goals.

Examples include:

Left hand:

- root emphasis
- octave spacing
- walking bass

Right hand:

- close voicing
- guide tones
- upper extensions
- melodic connection

These rules differ significantly from guitar while using the same harmonic plan.

---

# 8.14 Voice-Leading Score

Every generated progression may eventually receive an independent voice-leading score.

Possible contributors include:

- average movement distance
- common-tone preservation
- stepwise motion
- inversion quality
- spacing
- voice crossing
- parallel intervals

The resulting score complements harmonic confidence rather than replacing it.

---

# 8.15 Interaction with the Planning Engine

Planning determines the destination.

Voice leading determines the journey.

For example:

Planning:

```
Resolve to tonic.
```

Generation:

```
G7

↓

C
```

Voice leading:

```
F

↓

E

B

↓

C

D

↓

C

G

↓

G
```

The harmonic destination remains unchanged while individual voices move naturally.

---

# 8.16 Interaction with the Rhythm Engine

Voice leading and rhythm influence one another.

The same harmonic movement may be expressed as:

```
Whole notes
```

or

```
Arpeggios
```

or

```
Broken accompaniment
```

or

```
Walking bass
```

The Rhythm Engine therefore consumes the output of the Voice-Leading Engine rather than the harmonic planner directly.

---

# 8.17 Future Voice-Leading Algorithms

Several increasingly sophisticated approaches are planned.

### Classical optimisation

Applying traditional four-part harmony rules.

---

### Graph search

Finding the lowest-cost transition between voicings.

---

### Dynamic programming

Evaluating complete phrases rather than isolated transitions.

---

### Constraint solving

Balancing:

- movement,
- spacing,
- range,
- style,
- ergonomics,

simultaneously.

---

### Machine-learning assistance

Learning preferred voicings from musical corpora while preserving theoretical correctness.

---

# 8.18 Expressive Voice Leading

Beyond correctness lies expression.

Future versions may intentionally manipulate voice movement.

Examples include:

```
Smooth

↓

lyrical

↓

connected
```

versus

```
Angular

↓

dramatic

↓

restless
```

Different emotional objectives may therefore influence voice-leading decisions independently from harmonic planning.

---

# 8.19 Educational Value

Because every movement is calculated rather than hidden, ReasonTouch can explain voice-leading decisions.

Examples:

```
Common tones retained.

```

```
Bass moves by step.

```

```
First inversion chosen to avoid leap.

```

```
Parallel fifth avoided.

```

These explanations transform the engine into a teaching tool as well as a compositional assistant.

---

# 8.20 Long-Term Vision

Ultimately, the Voice-Leading Engine will become a reusable service shared across the entire ReasonTouch platform.

Future modules may include:

- automatic SATB writing,
- jazz piano voicings,
- orchestral reductions,
- guitar chord optimisation,
- choral arranging,
- string quartet generation,
- adaptive accompaniment.

Each module will employ different rendering rules while sharing the same harmonic intelligence.

---

# 8.21 Summary

Voice leading is the bridge between harmonic theory and musical performance.

By treating it as an independent architectural layer, ReasonTouch gains significant flexibility:

- harmonic planning remains instrument-independent,
- multiple voicing systems can coexist,
- educational explanations become possible,
- performance quality improves,
- future orchestration becomes straightforward.

As the project evolves, the Voice-Leading Engine will transform abstract harmonic progressions into musically convincing note-by-note movement, providing the foundation for expressive accompaniment, orchestration and ultimately complete musical realisation.
