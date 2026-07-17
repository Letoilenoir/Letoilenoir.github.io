# Chapter 4 — Progression Planning Architecture

**ReasonTouch Technical Companion**  
Version 1.0 (Working Draft)

---

# 4. Progression Planning Architecture

## 4.1 Introduction

If the Harmonic Analysis Engine answers the question

> *"What is this progression?"*

then the Progression Planning Architecture answers

> *"Where should this progression go next?"*

This distinction is fundamental to the design philosophy of ReasonTouch.

Traditional chord generators often skip directly from analysing the current chord to selecting the next one.

ReasonTouch deliberately inserts an intermediate planning layer.

Instead of:

```
Analyse

↓

Generate
```

ReasonTouch performs:

```
Analyse

↓

Plan

↓

Generate
```

This seemingly small architectural change produces a much more musical system.

The software is no longer choosing isolated chords.

It is making compositional decisions.

---

# 4.2 Why Planning Matters

Imagine a human composer writing the progression:

```
C

Am

F

G
```

They rarely think

> "What chord comes next?"

Instead they ask questions such as

- Should this section resolve?
- Should tension continue?
- Is this the end of a phrase?
- Should the music become more energetic?
- Is this leading into a chorus?
- Should I surprise the listener?

Only after deciding the musical intention do they begin selecting chords.

The Planning Layer attempts to model this same thought process.

---

# 4.3 Separation of Musical Intent and Musical Realisation

One of the most important design principles within ReasonTouch is separating **intent** from **implementation**.

The planner never thinks in terms of chord names.

Instead it thinks in terms of goals.

Examples include:

```
Continue

Resolve

Increase tension

Repeat motif

Extend phrase

Create contrast

Modulate

Prepare cadence
```

These intentions are independent of key.

Whether the progression is in

```
C Major
```

or

```
F# Minor
```

the planning logic remains identical.

Only later are these abstract goals converted into actual harmony.

---

# 4.4 Inputs to the Planner

The planner receives a complete musical description from the Harmonic Analysis Engine.

Primary input:

```kotlin
ProgressionAnalysis
```

Typical information includes:

- detected key
- cadence type
- harmonic stability
- harmonic functions
- tension
- energy
- root movement
- confidence
- progression length

Additional contextual inputs include:

- current workspace
- requested phrase length
- generation mode
- user preferences
- mood bias
- optional style constraints

Together these describe both the music and the composer's intentions.

---

# 4.5 Planner Responsibilities

The planner is responsible for deciding:

- whether the current phrase is complete
- whether continuation is appropriate
- whether resolution should occur
- whether repetition is desirable
- whether modulation is appropriate
- whether variation should increase
- how much harmonic risk is acceptable

Notice that none of these involve selecting actual chords.

Those decisions belong to the generation layer.

---

# 4.6 Planning Goals

Internally the planner produces one or more planning objectives.

Examples include:

```
Continue Naturally
```

```
Resolve
```

```
Increase Energy
```

```
Reduce Tension
```

```
Prepare Chorus
```

```
Extend Phrase
```

```
Create Contrast
```

```
Modulate
```

Each objective represents a possible future direction for the music.

The generator later determines how to realise that direction harmonically.

---

# 4.7 Multiple Future Possibilities

One of ReasonTouch's core principles is that music rarely has only one correct continuation.

Instead of producing:

```
Next Chord = G
```

the planner generates multiple possible futures.

For example:

```
Future A

Natural continuation
```

```
Future B

Strong cadence
```

```
Future C

Unexpected modulation
```

```
Future D

Increase emotional tension
```

Each represents a different compositional decision rather than merely a different chord.

This allows the user to remain the creative decision maker.

---

# 4.8 Planning Strategies

Planning behaviour is divided into independent strategy modules.

Examples include:

```
ContinueStrategy
```

```
ResolveStrategy
```

```
ContrastStrategy
```

```
RepeatStrategy
```

```
ExpandStrategy
```

```
BridgeStrategy
```

```
ModulationStrategy
```

Each strategy answers one specific question.

For example,

**ContinueStrategy**

asks

> "How can this idea continue naturally?"

whereas

**ContrastStrategy**

asks

> "How can the next phrase feel different while remaining related?"

Because these strategies are isolated they can evolve independently.

---

# 4.9 Strategy Selection

The planner does not execute every strategy equally.

Instead each strategy is scored according to the current analysis.

For example:

| Strategy | Score |
|----------|------:|
| Continue | 0.94 |
| Resolve | 0.82 |
| Contrast | 0.41 |
| Modulate | 0.08 |

These scores are influenced by:

- harmonic stability
- cadence type
- phrase length
- energy
- tension
- user mood bias
- historical context

The highest scoring strategies become generation candidates.

---

# 4.10 Phrase Awareness

Unlike many chord generators, ReasonTouch plans in phrases rather than individual chords.

Instead of asking

> "What is the next chord?"

the planner asks

> "What should the next four bars achieve?"

Typical phrase objectives include:

- reinforce tonic
- climb toward dominant
- prepare cadence
- delay resolution
- repeat previous idea
- answer previous phrase

This phrase-oriented approach produces significantly more coherent musical results.

---

# 4.11 Musical Memory

Future versions of the planner will maintain a larger compositional memory.

Rather than analysing only the current progression, the planner will remember:

- previous phrases
- repeated motifs
- harmonic rhythm
- previous cadences
- modulation history
- thematic material

This allows long-form composition rather than isolated progression generation.

---

# 4.12 Mood Bias Integration

The existing Mood Bias control naturally integrates into the planning layer.

Rather than simply altering chord probabilities, mood affects planning priorities.

For example:

Low mood bias may favour:

- slower resolutions
- suspended harmony
- modal colour
- descending movement

High mood bias may favour:

- stronger cadences
- brighter harmonic motion
- ascending progressions
- energetic transitions

This produces more coherent emotional development than merely changing chord weights.

---

# 4.13 Planning Output

The planner produces one or more planning requests.

Conceptually these resemble:

```kotlin
ProgressionGenerationRequest
```

Typical contents include:

```text
Source Analysis

Desired Direction

Preferred Length

Target Energy

Target Stability

Target Tension

Allowed Borrowed Chords

Generation Strategy
```

These requests are then passed to the generation engine.

The planner therefore acts as the bridge between musical understanding and musical creation.

---

# 4.14 Current Implementation

At present the planning architecture exists in a partially implemented form.

Components already present include:

- ContinueStrategy
- ProgressionGenerationRequest
- GeneratedProgression
- strategy interfaces
- harmonic analysis pipeline

Several additional planning strategies remain on the roadmap.

Current development is focused on completing the planning framework before expanding generation capabilities.

This ensures that future AI improvements build upon a stable and extensible architectural foundation.

---

# 4.15 Future Development

The planning layer is intended to become increasingly sophisticated over time.

Planned enhancements include:

### Adaptive Strategy Selection

Strategies will learn which continuations users prefer.

---

### Style Profiles

Different planning behaviours for:

- Classical
- Jazz
- Blues
- Pop
- Rock
- Folk
- Film
- Progressive

---

### Structural Awareness

Planning will understand:

- verses
- choruses
- bridges
- intros
- codas

---

### Emotional Arcs

Rather than planning individual phrases, the engine will eventually model complete emotional journeys across an entire composition.

---

### Long-Term Harmonic Planning

Future versions may plan:

```
8 bars

↓

16 bars

↓

32 bars

↓

Entire songs
```

before generating any individual chords.

This moves ReasonTouch beyond chord suggestion into true compositional assistance.

---

# 4.16 Summary

The Progression Planning Architecture is the intellectual centre of the ReasonTouch generation engine.

It transforms musical analysis into compositional intent.

Rather than asking

> "What chord comes next?"

it asks

> "Where should the music go?"

This distinction allows the software to behave less like a random chord generator and more like a collaborative musical partner.

By separating planning from generation, the system becomes easier to extend, easier to reason about, and capable of supporting increasingly sophisticated compositional techniques in future releases.

---

# End of Chapter 4

**Next Chapter**

**Chapter 5 — Chord Generation Engine**
