# Chapter 11 — Architecture Summary & Guiding Principles

> *ReasonTouch Technical Companion*  
> Version: Draft 1.0

---

# 11. Architecture Summary & Guiding Principles

---

## 11.1 Purpose of this Chapter

The previous chapters have described the individual systems that comprise ReasonTouch.

This final chapter steps back from implementation details and explains the architectural philosophy that ties the entire application together.

It answers a simple question:

> **Why has ReasonTouch been built this way?**

The answer is that the application is intended to remain maintainable, expandable, and musically correct over many years of development.

---

# 11.2 The Core Architectural Philosophy

ReasonTouch is founded upon five guiding principles:

1. **Musical correctness before convenience**
2. **Separation of responsibilities**
3. **Explainable behaviour**
4. **Incremental extensibility**
5. **User creativity remains central**

Every subsystem ultimately exists to support these principles.

---

# 11.3 Music Before Code

Many music applications begin with user interface design and later attempt to add theoretical understanding.

ReasonTouch takes the opposite approach.

The musical model is considered the primary source of truth.

Everything else exists to present, manipulate, analyse, or generate information from that model.

The dependency direction therefore becomes:

```
Music Theory

↓

Analysis

↓

Planning

↓

Generation

↓

User Interface
```

Never the reverse.

---

# 11.4 Domain-Driven Design

The project follows a domain-driven structure.

Rather than organising the code around Android components, it is organised around musical concepts.

Examples include:

```
TheoryChord

KeyCandidate

CadenceType

ProgressionAnalysis

GeneratedProgression

HarmonicFunction
```

These objects represent musical ideas rather than UI widgets.

As a result, the theory engine can eventually operate independently of Android.

---

# 11.5 Layer Separation

The application separates responsibilities into distinct architectural layers.

```
Presentation

↓

Workspace

↓

Planning

↓

Analysis

↓

Theory

↓

Rendering
```

Each layer knows only what it needs to know.

This prevents implementation details from leaking throughout the project.

---

## Presentation Layer

Responsible for:

- Compose UI
- dialogs
- interaction
- user workflow
- visual state

It should contain almost no musical logic.

---

## Workspace Layer

Responsible for:

- user editing
- progression construction
- workspace state
- interaction orchestration

This is where musical operations are requested—not performed.

---

## Planning Layer

Responsible for:

- selecting strategies
- choosing destinations
- building phrases
- recommending alternatives

This is the application's "musical brain."

---

## Analysis Layer

Responsible for interpreting existing music.

It answers questions such as:

- What key?
- What cadence?
- How stable?
- How much tension?
- What harmonic function?

Analysis never generates new music.

---

## Theory Layer

The foundation of the application.

Contains:

- scales
- intervals
- harmony
- functional relationships
- chord construction

Nothing above this layer should duplicate theoretical knowledge.

---

## Rendering Layer

Responsible for:

- MIDI
- notation
- diagrams
- piano roll
- guitar views

Rendering never changes musical meaning.

It merely displays it.

---

# 11.6 Single Responsibility Principle

Every major component should perform one task exceptionally well.

Examples:

```
KeyDetector

↓

Detects keys only.
```

```
CadenceDetector

↓

Recognises cadences only.
```

```
ChordSuggestionEngine

↓

Produces chord candidates only.
```

```
ProgressionPlanner

↓

Plans progressions only.
```

This makes each class easier to understand, test, and replace.

---

# 11.7 Explainability

ReasonTouch deliberately avoids becoming a "black box."

Whenever practical, recommendations should include explanations.

Instead of:

```
Suggested:

Am
```

the planner should eventually provide:

```
Suggested:

Am

Reason:

Acts as vi.

Provides gentle contrast.

Maintains tonic family.

Prepares ii naturally.
```

Every recommendation should be understandable.

---

# 11.8 Deterministic Musical Logic

The harmonic engine is intentionally deterministic.

Given identical inputs, it should produce identical outputs.

Benefits include:

- reproducibility
- testing
- educational consistency
- predictable behaviour

Creative variation should be introduced explicitly rather than through hidden randomness.

---

# 11.9 Controlled Creativity

ReasonTouch encourages exploration without sacrificing musical coherence.

Generation therefore balances:

```
Predictability

←────────────→

Novelty
```

User-adjustable parameters such as:

- surprise
- tension
- energy
- mood

allow creativity to be guided rather than left entirely to chance.

---

# 11.10 Data over Inheritance

Where practical, the architecture favours immutable data models over deep inheritance hierarchies.

For example:

```
GeneratedProgression
```

is a simple data object rather than a complex class hierarchy.

Advantages include:

- easier serialization
- simpler testing
- clearer APIs
- improved readability

---

# 11.11 Extensibility

Every major subsystem is designed so new functionality can be added without rewriting existing code.

For example:

New generation strategies should simply implement a common interface.

```
ContinueStrategy

ResolveStrategy

SurpriseStrategy

BridgeStrategy

JazzStrategy
```

can all coexist without modifying the planner itself.

The planner merely selects an appropriate strategy.

---

# 11.12 Future Independence

Several core systems have intentionally been written so they can eventually become independent libraries.

Potential standalone modules include:

```
Theory

Analysis

Planning

Rendering

Generation
```

This would allow future desktop, web, or server versions of ReasonTouch to reuse the same musical engine.

---

# 11.13 Testing Philosophy

Testing should occur at multiple levels.

### Unit Tests

Verify:

- interval calculations
- scale construction
- chord generation
- cadence recognition

---

### Integration Tests

Verify:

- progression planning
- analysis pipelines
- MIDI generation

---

### Musical Validation

Finally, every algorithm should be evaluated by musicians.

A technically correct progression is not necessarily a musically satisfying progression.

Human evaluation therefore remains essential.

---

# 11.14 Performance Philosophy

Efficiency is important, but readability takes priority.

The application analyses relatively small musical datasets.

Therefore:

- understandable algorithms
- maintainable code
- clear naming

are generally preferred over premature optimisation.

Optimisation should occur only where measurement demonstrates genuine need.

---

# 11.15 Documentation as Architecture

Documentation is considered part of the architecture.

Every significant subsystem should answer three questions:

1. What problem does it solve?
2. Why does it exist?
3. How does it interact with other systems?

This ensures that future contributors understand architectural intent rather than merely implementation details.

---

# 11.16 Maintaining Architectural Integrity

As the project grows, there is a natural temptation to place logic wherever it appears most convenient.

This must be resisted.

Musical rules belong in the theory and analysis layers.

Planning decisions belong in the planning layer.

Presentation concerns belong in the UI.

Maintaining these boundaries prevents architectural erosion and preserves long-term maintainability.

---

# 11.17 The Vision Realised

ReasonTouch is more than a chord generator.

It is intended to become an integrated musical reasoning system capable of:

- analysing harmony
- explaining theory
- planning progressions
- assisting composition
- generating performances
- educating musicians

Its architecture reflects this ambition.

Rather than building isolated features, the project establishes a coherent musical platform upon which increasingly sophisticated capabilities can be developed.

---

# Closing Remarks

The journey documented throughout this companion reflects a deliberate progression from theory to implementation, from individual chords to complete compositions, and from isolated algorithms to an integrated musical ecosystem. Every architectural decision has been guided by the belief that software should assist creativity without obscuring the underlying musical principles. By maintaining clear separation between theory, analysis, planning, generation, and presentation, ReasonTouch is positioned not merely as an application, but as a continually evolving platform for composition, education, and musical exploration.

This concludes the first edition of the **ReasonTouch Technical Companion**.
