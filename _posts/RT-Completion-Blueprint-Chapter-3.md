# ReasonTouch Completion Blueprint
## Chapter 3 — The Target Architecture

Version 1.0 (Draft)

---

# 1. Introduction

The architectural audit demonstrated that ReasonTouch does not require another major redesign.

Instead, it requires convergence.

Over time, numerous capable subsystems have been developed independently.

Each solved a particular problem well, but collectively they now form a partially connected network rather than a single reasoning engine.

The objective of the target architecture is therefore simple:

> Every musical decision should flow through one coherent chain of reasoning.

Rather than numerous independent generators making isolated decisions, the application will progressively narrow possibilities until a musically justified result is produced.

---

# 2. From Tool Collection to Musical Reasoning System

The earliest versions of ReasonTouch behaved as a collection of independent tools.

Examples included:

- Chord lookup
- Fingering selection
- Scale reference
- Progression editor
- Pattern generator

Each solved an isolated musical task.

As development progressed, additional intelligence was introduced.

Examples include:

- key detection
- harmonic analysis
- cadence identification
- phrase generation
- continuation suggestions

These systems introduced reasoning but still operated largely independently.

The Version 1 architecture transforms these into one integrated compositional workflow.

---

# 3. The Layered Architecture

The target architecture is intentionally divided into independent reasoning layers.

Each layer answers a different musical question.

```
User Action

↓

Progression Acquisition

↓

Musical Analysis

↓

Intent Recognition

↓

Phrase Planning

↓

Strategy Selection

↓

Chord Generation

↓

Voice Leading

↓

Presentation

↓

Export / Playback
```

Each layer is replaceable without affecting the others.

This greatly improves maintainability while allowing future enhancements.

---

# 4. Layer One — Progression Acquisition

Every reasoning process begins with musical context.

This layer gathers:

- current progression
- active key
- user settings
- selected workspace
- mood bias
- preferred style
- phrase length
- destination preferences

It answers one question:

> "What musical situation are we currently in?"

No musical decisions occur here.

Only context collection.

---

# 5. Layer Two — Musical Analysis

The analysis layer transforms raw musical data into meaningful information.

Existing components already provide much of this capability.

The output is represented primarily by:

```
ProgressionAnalysis
```

which contains information including:

- detected key

- cadence type

- harmonic stability

- energy

- tension

- ending function

- confidence

- harmonic movement

- functional sequence

This layer should become the single source of truth for all later planning decisions.

No downstream component should independently re-analyse the progression.

---

# 6. Layer Three — Intent Recognition

This layer does not ask:

> "What chord comes next?"

Instead it asks:

> "What is the user trying to achieve?"

Examples include:

Continue

Resolve

Build Tension

Surprise Me

Modulate

Repeat

Extend

Prepare Chorus

Bridge

Outro

The answer determines which planning engine will be invoked.

This represents one of the most important conceptual changes introduced by the audit.

---

# 7. Layer Four — Phrase Planning

This is the heart of the new architecture.

Instead of generating isolated chords, the planner constructs a musical destination.

For example:

```
Current:

ii → V

Goal:

Complete an authentic cadence

↓

Required destination:

I

↓

Possible routes:

ii–V–I

ii–V⁷–I

ii–V–Imaj7

ii–V–vi–IV–I
```

Notice that the planner does not yet choose specific voicings.

It only defines the musical route.

---

# 8. Layer Five — Strategy Selection

Once a destination has been identified, the planner chooses the most appropriate strategy.

Examples include:

Continue Strategy

Resolution Strategy

Tension Strategy

Surprise Strategy

Borrowed Chord Strategy

Modulation Strategy

Phrase Completion Strategy

Each strategy becomes a specialist.

Rather than every generator solving every musical problem, each becomes responsible for one compositional objective.

This greatly simplifies future maintenance.

---

# 9. Layer Six — Chord Generation

Only after the musical destination has been planned does chord generation begin.

Generation becomes considerably simpler because many decisions have already been made.

The generator receives information such as:

```
Destination:

Authentic Cadence

Target:

I

Allowed Functions:

Predominant

Dominant

Tonic

Preferred Length:

4 bars
```

It then constructs candidate phrases satisfying those constraints.

Generation therefore becomes constrained rather than random.

---

# 10. Layer Seven — Evaluation

Generated phrases should not be accepted immediately.

Each candidate should be evaluated against several criteria.

Examples include:

Harmonic correctness

Voice-leading quality

Cadential strength

Stylistic suitability

Tension curve

Phrase balance

Novelty

Confidence

Rather than returning one answer immediately, the planner should rank multiple candidates.

This naturally supports the four suggestion buttons already present within the interface.

---

# 11. Layer Eight — Explanation

One of the distinguishing characteristics of ReasonTouch should be explainability.

Every recommendation should be capable of answering:

Why?

Examples:

```
Chosen because it completes
a perfect authentic cadence.

Chosen because the dominant
requires tonic resolution.

Chosen because it increases
harmonic tension before
the chorus.

Chosen because it borrows
from the parallel minor.
```

This explanation layer is entirely absent from most commercial music software.

It has enormous educational value.

---

# 12. Layer Nine — Presentation

Only after reasoning is complete should the UI become involved.

The presentation layer converts planning results into workspace-specific formats.

Examples include:

Manual Workspace

Piano Roll

Phrase Cards

Suggestion Dialogs

Progression Pairing

Future Song Builder

Because presentation occurs last, the same planner can support multiple workspaces.

---

# 13. Layer Ten — Playback and Export

The final layer converts generated material into usable musical output.

Existing infrastructure already performs much of this work.

Outputs include:

MIDI

Piano Roll

Strumming Engine

Playback

Future notation

Future DAW export

Importantly, this layer should never influence planning.

Planning always precedes rendering.

---

# 14. Information Flow

The completed architecture therefore resembles a pipeline.

```
Current Progression

↓

Progression Analysis

↓

Intent Recognition

↓

Planner

↓

Strategy

↓

Phrase Generator

↓

Evaluation

↓

Explanation

↓

Workspace

↓

Playback
```

Information flows in one direction.

Later stages should not duplicate earlier analysis.

---

# 15. Architectural Principles

The audit established several guiding principles that all future development should follow.

## Single Source of Truth

Each musical fact should be calculated once.

Examples:

Key

Cadence

Progression analysis

Harmonic function

Subsequent layers consume these results rather than recalculating them.

---

## Separation of Concerns

Each layer performs exactly one responsibility.

Analysis analyses.

Planning plans.

Generation generates.

Presentation presents.

This keeps components small and understandable.

---

## Replaceability

Every planner should be replaceable without affecting other systems.

Future improvements should therefore require minimal modification elsewhere.

---

## Explainability

Every recommendation must eventually become explainable.

If the planner cannot explain a recommendation, it should be considered incomplete.

---

## Extensibility

The architecture must accommodate future systems without redesign.

Examples include:

- melody generation
- bass generation
- counterpoint
- orchestration
- AI-assisted composition
- adaptive tutoring

The layered architecture naturally supports these additions.

---

# 16. Relationship to the Completion Blueprint

This chapter defines the destination.

The remainder of the Blueprint explains how each architectural layer will be completed.

Every subsequent chapter represents one portion of this target architecture.

Rather than introducing new concepts, later chapters progressively populate the layers described here until the complete compositional engine emerges.

---

## Next Chapter

**Chapter 4 — The Progression Pairing Engine**

Having established the target architecture, the next chapter examines the first major subsystem identified during the audit: the Progression Pairing Engine.

This engine will become responsible for understanding how complete musical phrases connect together, providing the bridge between isolated chord progressions and coherent song construction.

---

_End of Chapter 3_
