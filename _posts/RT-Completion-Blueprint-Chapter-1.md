# ReasonTouch Completion Blueprint
## Chapter 1 — Introduction, Purpose and Philosophy

Version 1.0 (Draft)

---

# 1. Introduction

ReasonTouch has reached an important stage in its evolution.

The project is no longer a prototype, nor simply an Android application containing a collection of music-theory utilities.

It has become the foundation of a much larger system:

- a compositional assistant
- a harmonic reasoning engine
- an educational environment
- a musical planning system
- eventually a complete composition workstation.

The architectural audit carried out during development revealed something significant:

The majority of the required infrastructure already exists.

Many of the remaining tasks are not about inventing new systems but about connecting, completing and extending the systems that have already been designed.

This document records those findings.

It is intended to become the master construction blueprint for completing ReasonTouch.

---

# 2. Why This Blueprint Exists

During the architectural review a recurring pattern emerged.

Many modules already contain:

- interfaces
- data models
- analysis classes
- planning structures
- UI placeholders
- generation pipelines

but are not yet connected into a complete reasoning workflow.

In other places functionality has been implemented twice:

- an original implementation

and

- a newer planning implementation

which now need to be unified.

Without a structured roadmap it becomes increasingly difficult to determine:

- what should be built next
- what should be refactored
- what already exists
- what should be preserved
- what should eventually be removed.

This blueprint answers those questions.

---

# 3. Philosophy of Completion

The audit demonstrated an important principle that will govern the remainder of development.

> We are no longer writing isolated features.

Instead we are constructing an integrated musical reasoning system.

Every new component must therefore satisfy three requirements.

## 3.1 Musical Correctness

The system must continue to behave according to accepted principles of harmony.

Every decision should have a musical explanation.

The application should never become merely a random chord generator.

---

## 3.2 Explainability

Every recommendation should be capable of explaining itself.

The user should eventually be able to ask:

"Why was this suggested?"

and receive a meaningful answer.

This principle affects:

- continuation suggestions

- cadence planning

- modulation

- substitutions

- borrowed chords

- phrase generation

- composition planning.

---

## 3.3 Layered Reasoning

The audit established that musical reasoning occurs naturally in layers.

Rather than generating chords directly, ReasonTouch should reason through successive stages.

```
Current progression
        │
        ▼
Progression Analysis
        │
        ▼
Intent Recognition
        │
        ▼
Phrase Planning
        │
        ▼
Cadence Selection
        │
        ▼
Chord Generation
        │
        ▼
Voice-leading
        │
        ▼
Playback / Export
```

Each layer solves a different problem.

Each layer can later be improved independently.

---

# 4. The Current Position

At the conclusion of the audit the project can be summarised as follows.

## Completed Foundations

✔ Chord database

✔ Fingering engine

✔ Chord recognition

✔ Progression editor

✔ Piano Roll

✔ MIDI export

✔ Strumming engine

✔ Key detection

✔ Harmonic function detection

✔ Progression analysis

✔ Generation request model

✔ Generation strategies

✔ Planning interfaces

✔ Suggestion engine

✔ Workspace architecture

These form a remarkably complete foundation.

---

## Partially Complete Systems

The following systems exist but require completion.

- Progression pairing

- Phrase continuation

- Intelligent cadence planning

- Borrowed chord planning

- Modulation planning

- Style-aware generation

- Voice-leading optimisation

- Explanation engine

- Adaptive composition planning

---

## Future Systems

These are intentionally outside Version 1 but have already influenced today's architecture.

- Full AI composition assistant

- Song structure generation

- Counterpoint assistant

- Melody planning

- Automatic accompaniment

- Interactive tutoring

- Real-time harmonic coaching

---

# 5. The Audit's Most Important Discovery

Perhaps the most significant discovery made during the audit was that ReasonTouch already contains the beginnings of a genuine planning engine.

Originally the application generated the "next chord."

The newer architecture instead reasons about:

- harmonic destination

- cadence type

- functional movement

- progression intent

- phrase direction

This changes the entire philosophy of the software.

Instead of asking

> "What chord comes next?"

ReasonTouch increasingly asks

> "Where is this music trying to go?"

Only after answering that question does it determine which chord should appear next.

This represents a fundamental shift from reactive generation to intentional composition.

---

# 6. Development Strategy Going Forward

The audit recommends that all remaining work follows a simple rule.

Complete systems vertically rather than horizontally.

Instead of adding isolated features across many modules, development should focus on completing one reasoning pipeline at a time.

For example:

```
Analyse
↓

Determine intent

↓

Plan destination

↓

Generate phrase

↓

Explain phrase

↓

Return result
```

Only after one pipeline is complete should the next reasoning pipeline begin.

This produces working musical intelligence earlier while reducing architectural debt.

---

# 7. Blueprint Structure

The remainder of this Blueprint is organised into progressive construction phases.

Rather than describing source code files, each chapter describes one complete subsystem.

These chapters collectively define the roadmap toward Version 1.

The planned sequence is:

1. Progression Pairing Engine

2. Continue Path

3. Resolution Path

4. Tension Builder

5. Surprise Generator

6. Phrase Planner

7. Cadence Engine

8. Borrowed Chord Planner

9. Modulation Planner

10. Voice-leading Engine

11. Musical Explanation Layer

12. Integration Architecture

13. Testing Strategy

14. Version 1 Completion Roadmap

Each chapter builds upon those before it.

Together they define the construction plan for completing ReasonTouch.

---

_End of Chapter 1_
