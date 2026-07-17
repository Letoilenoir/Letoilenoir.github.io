# Chapter 2 – Progression Analysis Engine
*Technical Companion to the ReasonTouch Harmonic Intelligence Architecture*

---

# 2.1 Purpose

The Progression Analysis Engine is the first genuinely intelligent layer within
ReasonTouch.

While the chord database understands individual chords, and the progression
builder records sequences of chords, the analysis engine attempts to answer a
fundamentally different question:

> **What is this progression actually doing?**

Rather than treating a progression as nothing more than a list of chord names,
the engine interprets it as harmonic movement.

It determines:

- Probable key
- Harmonic function
- Cadence type
- Harmonic stability
- Harmonic tension
- Musical energy
- Structural behaviour

This analysis becomes the common language spoken by every higher-level
generation engine.

Instead of multiple generators attempting to analyse harmony independently,
they all consume the same immutable `ProgressionAnalysis` object.

The result is a consistent musical understanding throughout the entire
application.

---

# 2.2 Architectural Position

```
Chord Entry
      │
      ▼
Progression Builder
      │
      ▼
Progression Analysis Engine
      │
      ▼
ProgressionAnalysis
      │
      ├──────── Phrase Generator
      ├──────── Continuation Engine
      ├──────── Progression Pairing Engine
      ├──────── Cadence Generator
      ├──────── Variation Generator
      ├──────── AI Composition Assistant
      └──────── Future Machine Learning Systems
```

The Progression Analysis Engine therefore forms the bridge between raw musical
data and musical reasoning.

Everything above this layer operates on *meaning* rather than chord names.

---

# 2.3 Inputs

The engine accepts a completed progression.

Internally this may exist as either

```kotlin
List<String>
```

or

```kotlin
List<TheoryChord>
```

depending upon where the request originates.

For example:

```
C
Am
Dm
G
```

No assumptions are made about progression length.

A single bar can be analysed.

A complete song can be analysed.

The same algorithms operate regardless of size.

---

# 2.4 Analysis Pipeline

The analysis engine performs several distinct passes.

Each pass extracts increasingly sophisticated musical information.

---

## Stage 1 — Key Detection

The first objective is determining the most probable tonal centre.

Unlike traditional software, ReasonTouch deliberately avoids assuming that the
user already knows the key.

Instead, multiple candidate keys are scored.

Example:

```
C Major      Confidence 0.91
A Minor      Confidence 0.74
G Major      Confidence 0.48
```

This probabilistic approach reflects real music, where multiple interpretations
are often valid.

The strongest candidate becomes the working key while the remaining candidates
remain available for future analysis.

---

## Stage 2 — Harmonic Function Mapping

Every chord is mapped to its harmonic role.

Example progression:

```
C
Am
Dm
G
```

becomes

| Chord | Function |
|--------|----------|
| C | TONIC |
| Am | TONIC SUBSTITUTE |
| Dm | SUBDOMINANT |
| G | DOMINANT |

Internally this becomes

```kotlin
List<HarmonicFunction>
```

Example

```kotlin
[
    TONIC,
    TONIC,
    SUBDOMINANT,
    DOMINANT
]
```

Notice that from this point onwards the engine reasons about harmonic behaviour
rather than chord spelling.

This abstraction is fundamental to every later planning engine.

---

## Stage 3 — Root Motion Analysis

The engine measures movement between consecutive chord roots.

Examples include

- Ascending Fifth
- Descending Fifth
- Ascending Step
- Descending Step
- Chromatic Movement
- Repeated Root

Internally these become interval values.

Example

```kotlin
listOf(
    +7,
    -5,
    +2
)
```

Root movement later influences:

- progression continuation
- phrase generation
- cadence recognition
- similarity matching

---

## Stage 4 — Cadence Detection

One of the most important musical observations concerns how the progression
ends.

ReasonTouch currently recognises:

- Perfect Authentic Cadence
- Imperfect Authentic Cadence
- Half Cadence
- Plagal Cadence
- Deceptive Cadence
- Open Ending
- Unknown

Example

```
Dm → G
```

is recognised as a Half Cadence.

Whereas

```
G → C
```

is recognised as an Authentic Cadence.

Cadence information has a major influence on later suggestion generation.

---

## Stage 5 — Harmonic Stability

Rather than simply deciding whether a progression is "resolved" or
"unresolved", ReasonTouch represents stability as a continuous value.

```
0.0  Highly unstable

0.5  Transitional

1.0  Completely resolved
```

Typical examples

| Chord | Approximate Stability |
|--------|-----------------------|
| I | 1.00 |
| vi | 0.70 |
| ii | 0.45 |
| V | 0.25 |

This value becomes one of the most important planning signals throughout the
generation engine.

---

## Stage 6 — Musical Energy

Energy estimates how active the progression feels.

Unlike tempo or dynamics, this refers purely to harmonic activity.

Factors include

- dominant density
- functional movement
- cadence strength
- progression direction
- harmonic rhythm

Energy is represented as

```
0.0 → Calm

1.0 → Highly Active
```

The measurement is intentionally heuristic rather than academically absolute.

Its purpose is to create musically convincing suggestions.

---

## Stage 7 — Harmonic Tension

Tension estimates how strongly the harmony encourages continuation.

Examples

| Chord | Typical Tension |
|--------|-----------------|
| I | Low |
| vi | Low |
| ii | Moderate |
| IV | Moderate |
| V7 | High |

Tension is not the opposite of stability.

A progression may be relatively stable while simultaneously building tension
towards a larger structural resolution.

Keeping these measurements separate produces more natural generation later.

---

# 2.5 The ProgressionAnalysis Object

All stages ultimately produce a single immutable analysis object.

```kotlin
data class ProgressionAnalysis(

    val key: KeyCandidate,

    val cadenceType: CadenceType,

    val harmonicStability: Float,

    val energy: Float,

    val tension: Float,

    val endingFunction: HarmonicFunction,

    val rootMovementIntervals: List<Int>,

    val barCount: Int,

    val confidence: Float = 1.0f,

    val functionalSequence: List<HarmonicFunction>

)
```

This object intentionally contains **only musical information**.

It contains:

- no UI data
- no colours
- no localisation
- no display strings
- no Compose dependencies

Its sole purpose is to describe harmonic behaviour.

---

# 2.6 Why Every Generator Depends Upon It

Before introducing this architecture, each intelligent subsystem attempted to
perform its own harmonic analysis.

The continuation engine guessed the key.

Cadence generation guessed the harmonic direction.

Phrase generation estimated stability independently.

This duplicated code throughout the application.

More importantly, different systems frequently reached different conclusions.

The `ProgressionAnalysis` object solved this problem.

Every intelligent component now begins from exactly the same understanding of
the music.

As a result:

- behaviour is more consistent
- algorithms become smaller
- testing becomes easier
- future improvements automatically benefit every subsystem

The analysis layer therefore represents a central architectural decision rather
than simply another utility class.

---

# 2.7 Planned Extensions

The current model intentionally leaves room for considerably richer analysis.

Future additions may include

- modulation detection
- borrowed chord recognition
- modal interchange
- secondary dominant analysis
- tritone substitution detection
- phrase segmentation
- voice-leading quality
- emotional profile
- stylistic fingerprinting
- machine-learning confidence metrics

These additions can be incorporated without changing the external interface used
by the planning engines.

The analysis object has therefore been designed as a stable long-term contract.

---

# 2.8 Design Philosophy

Most music software asks:

> **Which chord comes next?**

ReasonTouch asks a more important question first:

> **What is this progression trying to achieve?**

Only after understanding the musical intent does the software begin generating
possible continuations.

This distinction marks the transition from a chord database to a genuine
composition assistant.

The Progression Analysis Engine therefore represents the foundation upon which
all future harmonic intelligence within ReasonTouch is built.

---

# End of Chapter 2

**Next Chapter**

**Chapter 3 – Harmonic Function Model & Functional Flow**

This chapter explores how harmonic functions are represented internally,
how functional movement is interpreted, and how these concepts drive the
Progression Pairing Engine and all subsequent composition strategies.
