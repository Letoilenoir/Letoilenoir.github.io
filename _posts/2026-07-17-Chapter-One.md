# ReasonTouch Harmonic Intelligence Architecture
# Software Architecture Specification

Version 1.0 (Draft)

---

# Chapter 1

# Vision, Objectives and Architectural Philosophy

---

# 1.1 Introduction

ReasonTouch began life as a chord dictionary and progression creation environment.

Over time it has evolved into something considerably more ambitious.

The long-term vision is no longer simply to assist users in selecting chords. Instead, ReasonTouch is intended to become an intelligent musical partner capable of understanding harmonic context, recognising musical intention, planning future development, and generating coherent musical ideas while remaining transparent about the reasoning behind every suggestion.

This document defines the architecture required to achieve that vision.

---

# 1.2 Project Vision

The ultimate goal is to create a compositional engine that behaves less like a random chord generator and more like an experienced musician.

When presented with a progression such as

    C  Am  F  G

the system should not simply return a statistically likely next chord.

Instead it should first understand:

• What key is implied?

• What harmonic function is each chord performing?

• Is the progression stable?

• Does it feel complete?

• Is it increasing or reducing tension?

• Does it sound like the end of a phrase?

• What musical expectations has it created?

Only after answering these questions should the engine decide what should happen next.

The distinction is fundamental.

ReasonTouch should generate music with intention rather than probability.

---

# 1.3 Guiding Philosophy

The architecture follows one simple principle:

> Never generate until you understand.

Every stage of the system therefore performs a distinct task.

Rather than allowing generation code to inspect raw chords directly, every decision should be based upon an analysed musical description.

This separates musical reasoning from musical generation.

Consequently:

Raw Chords

↓

Musical Analysis

↓

Planning

↓

Strategy Selection

↓

Generation

↓

Presentation

Every layer has exactly one responsibility.

---

# 1.4 The Difference Between Generation and Planning

Most progression generators combine these two concepts.

ReasonTouch deliberately separates them.

Planning answers:

"What should happen?"

Generation answers:

"How should it happen?"

Example:

Input

    C  Am  F  G

Planner:

    Continue naturally.

Generator:

    Em  Am  Dm  G

Different generator:

    C/E  F  Dm7  G7

Both satisfy exactly the same plan.

Separating planning from generation allows multiple musical interpretations of the same intention.

---

# 1.5 Design Goals

The Harmonic Intelligence subsystem has seven primary objectives.

## Goal 1

Understand before generating.

The engine should never recommend music it has not analysed.

---

## Goal 2

Explain every decision.

Every suggestion should have an explanation.

Example

"This progression ends on the dominant, suggesting continuation toward tonic resolution."

If the software cannot explain why it generated something, the design should be reconsidered.

---

## Goal 3

Maintain musical coherence.

Suggestions should feel like natural continuations rather than isolated chord substitutions.

The engine should think in phrases rather than individual chords.

---

## Goal 4

Separate responsibilities.

Analysis must never generate.

Generation must never analyse.

Planning must never render UI.

Each subsystem owns one responsibility only.

---

## Goal 5

Remain extensible.

The architecture should permit:

• Jazz

• Classical

• Folk

• Blues

• Film music

• Pop

without redesign.

New musical styles should be implemented through strategies rather than modifications to existing code.

---

## Goal 6

Remain deterministic.

Where possible identical inputs should produce identical outputs.

Randomness should exist only where explicitly requested.

This greatly improves:

• debugging

• testing

• explainability

---

## Goal 7

Prepare for future AI integration.

Artificial Intelligence should become another planning strategy rather than replacing the architecture.

Large language models or neural generators should consume ProgressionAnalysis objects rather than raw chord lists.

This preserves architectural consistency regardless of implementation technology.

---

# 1.6 Core Architectural Principles

The system follows several software engineering principles.

## Principle 1

Single Responsibility

Every subsystem performs one task.

Example

ProgressionAnalysis analyses.

ProgressionPlanner plans.

ContinueStrategy generates.

ChordWorkspace displays.

---

## Principle 2

Dependency Direction

Knowledge always flows downward.

UI

↓

Planner

↓

Analysis

↓

Theory

Theory never depends upon UI.

Generation never depends upon Compose.

Analysis never depends upon rendering.

---

## Principle 3

Replaceability

Any planning engine should be replaceable.

Examples

Rule-based planner

↓

Machine-learning planner

↓

AI planner

↓

Cloud planner

The remainder of the application should not require modification.

---

## Principle 4

Explainability

Every recommendation should expose its reasoning.

Example

Generated Phrase

↓

Planning Goal

↓

Musical Evidence

↓

Analysis

↓

Original Progression

The reasoning chain should always remain recoverable.

---

# 1.7 Architectural Layers

The complete subsystem is divided into seven layers.

──────────────────────────────

Layer 7

User Interface

──────────────────────────────

Displays results.

No musical reasoning.

──────────────────────────────

Layer 6

Presentation

──────────────────────────────

Converts generated data into UI models.

──────────────────────────────

Layer 5

Generation

──────────────────────────────

Produces TheoryChord objects.

──────────────────────────────

Layer 4

Planning

──────────────────────────────

Chooses musical intentions.

──────────────────────────────

Layer 3

Pairing

──────────────────────────────

Matches phrases.

──────────────────────────────

Layer 2

Analysis

──────────────────────────────

Produces ProgressionAnalysis.

──────────────────────────────

Layer 1

Theory

──────────────────────────────

Musical facts.

Intervals.

Scales.

Chord definitions.

Roman numerals.

No business logic.

---

# 1.8 System Overview

The complete reasoning pipeline can be visualised as follows.

                    Progression

                          │

                          ▼

              ProgressionAnalysis

                          │

                          ▼

               ProgressionPlanner

                          │

                          ▼

             ProgressionPairingEngine

                          │

                          ▼

              Generation Strategies

                          │

                          ▼

              Candidate Progressions

                          │

                          ▼

               Ranking & Explanation

                          │

                          ▼

                        User

Notice that generation is almost at the bottom of the pipeline.

The majority of the intelligence lies before any chord is produced.

---

# 1.9 Why This Architecture?

Traditional progression generators ask:

"What chord usually follows G?"

ReasonTouch instead asks:

"What is the current musical situation?"

Only after understanding the musical situation does it ask:

"What should happen?"

Finally it asks:

"Which chords best accomplish that?"

This mirrors the reasoning process of experienced musicians.

---

# 1.10 Scope

This specification covers the complete Harmonic Intelligence subsystem.

It does not specify:

• Piano Roll implementation

• MIDI playback

• Audio rendering

• User interface design

• File management

• Android lifecycle

These are consumers of the subsystem rather than part of it.

---

# 1.11 Success Criteria

The architecture will be considered successful when it satisfies the following conditions.

✓ The engine explains every suggestion.

✓ Planning is independent of generation.

✓ Strategies are independently replaceable.

✓ Harmonic analysis is reusable.

✓ Phrase pairing operates independently.

✓ Future AI systems plug into existing interfaces.

✓ New musical styles require no architectural redesign.

---

# 1.12 Conclusion

The Harmonic Intelligence subsystem represents the intellectual core of ReasonTouch.

Rather than acting as a chord recommender, it is designed to become a reasoning engine capable of analysing, planning, generating and explaining music in a way that mirrors the thought process of an experienced composer.

All subsequent chapters build upon the architectural philosophy established here.
