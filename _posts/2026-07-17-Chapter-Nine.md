# Chapter 9 – Musical Knowledge Representation

> *ReasonTouch Technical Companion*  
> Chapter 9

---

# 9. Musical Knowledge Representation

## 9.1 Introduction

Every intelligent software system depends upon how it represents knowledge.

In a spreadsheet, knowledge is represented as rows and columns.

In a relational database, it is represented through tables and relationships.

In an expert system, it is represented through rules.

ReasonTouch faces a more complex challenge.

Music is not merely data.

It is a network of relationships, hierarchies, functions, probabilities and contextual meaning.

The same chord can perform different harmonic functions depending upon its surrounding musical environment.

The purpose of the Musical Knowledge Representation layer is therefore to model music in a form that computers can reason about while remaining faithful to established music theory.

---

# 9.2 Data versus Knowledge

One of the earliest architectural decisions was to distinguish between musical **data** and musical **knowledge**.

For example,

```
Chord:

G7
```

is data.

Knowing that

```
G7

↓

C
```

forms a dominant-to-tonic resolution is knowledge.

ReasonTouch stores both.

The software therefore does not merely know chord names.

It understands what those chords represent.

---

# 9.3 Hierarchical Representation

Musical concepts exist at different levels.

```
Composition

↓

Section

↓

Phrase

↓

Progression

↓

Chord

↓

Intervals

↓

Individual Notes
```

Each layer contains information unavailable at the layer beneath it.

For example:

A note has no harmonic function.

A chord does.

A progression possesses cadence.

A phrase possesses direction.

A composition possesses form.

ReasonTouch therefore models music hierarchically.

---

# 9.4 Theory Objects

Rather than passing primitive values throughout the application,

ReasonTouch increasingly relies upon specialised theory objects.

Examples include:

```
TheoryChord

KeyCandidate

ProgressionAnalysis

GeneratedProgression

HarmonicFunction

CadenceType
```

These objects encapsulate musical meaning rather than raw data.

---

# 9.5 Chords as Objects

A chord is more than its printed name.

Internally it may contain:

```
Display label

Root note

Quality

Intervals

Chord tones

Extensions

Alterations

Enharmonic spelling

Playable voicings
```

Different modules may access different aspects without duplicating information.

---

# 9.6 Harmonic Function

Instead of repeatedly asking:

```
Is this G?
```

ReasonTouch asks:

```
Is this functioning as Dominant?
```

This abstraction dramatically simplifies reasoning.

For example,

```
G

↓

C
```

and

```
D

↓

G
```

share identical functional behaviour despite different chord names.

The reasoning engine therefore operates primarily on functions rather than labels.

---

# 9.7 Keys as Musical Context

Keys are represented as complete musical environments.

Rather than storing only:

```
C Major
```

the object may include:

```
Scale degrees

Diatonic chords

Accidentals

Relative key

Parallel key

Modal variants

Confidence
```

This richer representation supports far more sophisticated reasoning.

---

# 9.8 Progressions as First-Class Objects

A progression is not merely a list of chords.

It possesses independent characteristics.

Examples include:

```
Length

Cadence

Energy

Stability

Tension

Root movement

Functional sequence

Confidence
```

Treating progressions as independent musical entities enables higher-level planning.

---

# 9.9 Musical Relationships

ReasonTouch places significant emphasis on relationships rather than isolated objects.

Examples include:

```
Chord

↓

Function
```

```
Chord

↓

Key
```

```
Chord

↓

Voice-leading
```

```
Phrase

↓

Cadence
```

```
Phrase

↓

Section
```

The resulting knowledge graph is considerably richer than a simple collection of chord names.

---

# 9.10 Enumerations versus Objects

Simple musical concepts are represented using enumerations.

Examples:

```
CadenceType

HarmonicFunction

Mode

IntervalQuality
```

More complex concepts become dedicated objects.

Examples:

```
TheoryChord

GeneratedProgression

ProgressionAnalysis
```

This distinction keeps the architecture both expressive and maintainable.

---

# 9.11 Confidence as Metadata

Almost every analytical object may contain confidence.

For example:

```
KeyCandidate

Confidence

0.91
```

or

```
ProgressionAnalysis

Confidence

0.83
```

Confidence is treated as metadata rather than replacing musical certainty.

It allows later reasoning stages to make informed decisions under ambiguity.

---

# 9.12 Context Preservation

Musical objects rarely exist independently.

A chord derives meaning from:

- previous chords,
- following chords,
- detected key,
- phrase location,
- cadence,
- planning objective.

ReasonTouch therefore avoids stripping objects of their context unnecessarily.

Instead, contextual information is preserved throughout the reasoning pipeline.

---

# 9.13 Immutable Musical Objects

Where practical, theory objects are immutable.

Rather than modifying an object directly,

new versions are created.

Example:

```
Original Analysis

↓

Updated Analysis

↓

Revised Analysis
```

This approach offers several advantages:

- safer concurrency,
- easier debugging,
- predictable state,
- reproducible analysis.

It also aligns naturally with Kotlin's data class architecture.

---

# 9.14 Separation of Musical Domains

ReasonTouch deliberately separates different musical domains.

Examples include:

```
Harmony

Rhythm

Melody

Arrangement

Performance

Notation
```

Although these domains interact,

each maintains its own internal representation.

This reduces coupling while improving long-term extensibility.

---

# 9.15 Knowledge Evolution

Musical knowledge is expected to evolve throughout the project.

Early implementations focus primarily upon:

- tonal harmony,
- functional analysis,
- classical cadences.

Future expansions may introduce:

```
Jazz harmony

Modal theory

Film scoring

Extended chords

Quartal harmony

Polytonality

Contemporary harmony
```

The representation layer has therefore been designed for expansion rather than completeness.

---

# 9.16 Educational Metadata

One long-term objective is that every musical object should be capable of explaining itself.

For example,

a chord may eventually provide:

```
Function

Dominant
```

```
Scale Degree

V
```

```
Roman Numeral

V7
```

```
Suggested Resolution

I
```

```
Common Usage

Authentic cadence
```

This metadata transforms internal theory objects into educational resources.

---

# 9.17 Interoperability

The representation layer serves every subsystem.

Examples include:

```
Analysis

↓

Planning

↓

Generation

↓

Voice Leading

↓

Playback

↓

Notation
```

Because every module shares identical theory objects,

translation between systems becomes unnecessary.

This significantly reduces duplication throughout the application.

---

# 9.18 Towards a Musical Knowledge Graph

As ReasonTouch matures,

the representation layer increasingly resembles a knowledge graph.

Relationships may eventually include:

```
Chord

↓

Related Cadences

↓

Typical Resolutions

↓

Borrowed Variants

↓

Historical Usage

↓

Genre Frequency

↓

Difficulty
```

Such a graph enables reasoning well beyond traditional chord lookup.

---

# 9.19 Future Semantic Reasoning

Future versions may allow reasoning over musical concepts rather than explicit rules.

For example:

```
Find progressions

that gradually increase tension

while remaining modal

and avoiding authentic cadence.
```

Rather than executing fixed algorithms,

the engine queries relationships within the musical knowledge model.

This represents a significant step toward semantic musical intelligence.

---

# 9.20 Relationship to Artificial Intelligence

Machine learning performs best when built upon strong symbolic representations.

ReasonTouch therefore adopts a hybrid philosophy.

```
Symbolic Music Theory

+

Probabilistic Reasoning

+

Artificial Intelligence
```

Rather than replacing music theory,

AI will operate upon carefully structured musical knowledge.

This preserves explainability while enabling increasingly sophisticated compositional assistance.

---

# 9.21 Design Principles

The Musical Knowledge Representation layer follows several guiding principles.

### Music before implementation

Objects should represent musical ideas rather than programming convenience.

---

### Rich semantics

Every object should possess meaningful musical context.

---

### Immutability where practical

Theory objects should remain predictable throughout the reasoning process.

---

### Extensibility

Future theoretical concepts should integrate naturally without redesigning the architecture.

---

### Explainability

Every internal representation should ultimately support educational feedback.

---

# 9.22 Summary

The Musical Knowledge Representation layer forms the intellectual foundation of ReasonTouch.

Rather than treating music as disconnected chord names or note values, it models musical concepts as rich, interconnected objects capable of supporting analysis, planning, generation and explanation.

This symbolic representation enables ReasonTouch to reason about music in a manner that more closely resembles the thinking of trained musicians, while providing a robust foundation for future AI-assisted composition, orchestration and musical education.
