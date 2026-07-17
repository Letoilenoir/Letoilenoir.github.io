# ReasonTouch Completion Blueprint
## Chapter 2 — Architectural Audit Findings

Version 1.0 (Draft)

---

# 1. Purpose of the Audit

Before embarking on the completion of ReasonTouch, a comprehensive architectural audit was undertaken.

The objective was not simply to locate defects or obsolete code, but to determine whether the application's existing architecture remained suitable for the long-term vision of the project.

Specifically, the audit sought to answer five questions:

- What components already exist?
- Which components are production-ready?
- Which components overlap in responsibility?
- Which components should be preserved?
- What is the shortest path to a stable Version 1.0?

Unlike many software audits that culminate in recommendations for extensive rewrites, this audit reached a markedly different conclusion.

The core architecture of ReasonTouch is fundamentally sound.

The remaining work lies primarily in integration, refinement, and completion rather than replacement.

---

# 2. General Assessment

The audit revealed that the project is considerably more mature than its current feature set might initially suggest.

Beneath the user interface exists a substantial collection of reusable musical reasoning components, many of which have already evolved beyond the needs of the current application.

The project already contains:

- a comprehensive music theory model
- harmonic analysis capabilities
- progression analysis
- key detection
- cadence recognition
- generation strategies
- planning abstractions
- MIDI infrastructure
- Piano Roll integration
- workspace architecture

Collectively, these form the foundations of a true compositional engine rather than a simple chord reference application.

---

# 3. Major Strengths

## 3.1 Strong Domain Model

Perhaps the greatest strength of the project is its domain model.

Musical concepts are represented explicitly rather than inferred indirectly.

Examples include:

- TheoryChord
- KeyCandidate
- HarmonicFunction
- ProgressionAnalysis
- CadenceType
- Roman numerals
- Scale representations
- Interval calculations

This provides an excellent foundation for future reasoning systems.

---

## 3.2 Separation Between Theory and Interface

The audit confirmed that musical knowledge is largely independent of the user interface.

The theory engine does not depend upon:

- Jetpack Compose
- Android Views
- UI state
- display logic

This separation greatly improves:

- maintainability
- testing
- portability

It also makes future desktop or web versions significantly easier to develop.

---

## 3.3 Workspace Architecture

The application's workspace model has matured well.

Different creative tasks are naturally separated into dedicated environments while still sharing common infrastructure.

Current workspaces include:

- Manual Chord Workspace
- Piano Roll
- Pattern Selection
- Progression Editing

This architecture scales naturally as additional creative workflows are introduced.

---

## 3.4 Existing Planning Infrastructure

One of the most significant discoveries was that planning infrastructure already exists.

Classes such as:

- ProgressionGenerationRequest
- GeneratedProgression
- generation strategies

represent the beginnings of a true planning layer.

Although currently underutilised, these components provide an ideal foundation for intelligent progression generation.

---

# 4. Existing Weaknesses

The audit also identified several recurring architectural problems.

Importantly, these are problems of organisation rather than design.

---

## 4.1 Multiple Suggestion Pipelines

Chord suggestions currently originate from more than one location.

Examples include:

- legacy suggestion logic

- planner-based generation

- ViewModel helper methods

- workspace-specific suggestion routines

Although each functions independently, they duplicate responsibility.

This fragmentation makes future enhancements unnecessarily difficult.

The audit therefore recommends converging upon a single planning pipeline.

---

## 4.2 Duplicate Progression Generation

Several components independently generate progressions.

While developed at different stages of the project, they now overlap considerably.

This duplication introduces:

- inconsistent behaviour
- duplicated maintenance
- differing confidence calculations
- inconsistent explanations

The long-term objective should be one unified generation engine serving all workspaces.

---

## 4.3 Large ViewModels

Some ViewModels have gradually accumulated responsibilities beyond state management.

They currently perform tasks including:

- analysis
- planning
- generation
- formatting
- orchestration
- UI state management

Although functional, this makes future expansion increasingly difficult.

Planning logic should gradually migrate into dedicated planner classes.

---

## 4.4 Incomplete Planning Layer

The planning architecture is present but incomplete.

Current planning generally begins after the user has requested a suggestion.

The intended architecture instead performs several reasoning stages before any chord generation begins.

This missing layer is the primary focus of the Completion Blueprint.

---

# 5. Components Identified for Preservation

One of the principal objectives of the audit was determining which systems should *not* be rewritten.

The following components are considered stable architectural assets.

---

## Music Theory Engine

Retain.

Its abstractions remain appropriate and extensible.

---

## Harmonic Analysis

Retain.

Future planners should consume its results rather than replacing its functionality.

---

## Progression Analysis

Retain.

This class becomes central to all planning decisions.

---

## Key Detection

Retain.

Future improvements should enhance scoring rather than replace the detection model.

---

## Piano Roll

Retain.

The Piano Roll is already a capable editing environment and should continue to receive generated material from the planning layer.

---

## MIDI Infrastructure

Retain.

The export pipeline is independent, mature, and reusable.

---

## Workspace Framework

Retain.

The workspace concept remains well suited to ReasonTouch's long-term vision.

---

# 6. Components Identified for Refactoring

Unlike preserved systems, the following areas should evolve during completion.

These are evolutionary changes rather than complete rewrites.

---

## Suggestion Engine

Consolidate into a single planning entry point.

---

## Generation Strategies

Expand into richer planning strategies.

---

## Phrase Construction

Move from procedural generation towards destination-driven planning.

---

## ViewModel Responsibilities

Reduce orchestration complexity.

Delegate reasoning to planner components.

---

## Confidence Scoring

Unify confidence calculations across all generation strategies.

---

## Explanation Generation

Introduce a shared explanation engine rather than generating descriptive text independently within each feature.

---

# 7. The Central Architectural Discovery

The most valuable conclusion reached during the audit can be summarised simply.

ReasonTouch does **not** require a new architecture.

It requires completion of the architecture that already exists.

This distinction fundamentally changes the remainder of development.

Instead of replacing systems, we will:

- connect them
- simplify them
- remove duplication
- complete unfinished planning layers
- extend existing abstractions

This dramatically reduces technical risk while preserving the investment already made in the project.

---

# 8. The Decision to Build Vertically

The audit recommends abandoning feature-by-feature development.

Instead, the remainder of Version 1 should be completed vertically.

A complete reasoning path should be finished before beginning another.

For example:

```
User presses Continue

↓

Analyse progression

↓

Determine harmonic intent

↓

Select planning strategy

↓

Generate candidate phrases

↓

Evaluate confidence

↓

Explain recommendations

↓

Display results
```

Only when this entire pipeline is complete should the next pathway (such as Resolve or Build Tension) begin.

This approach ensures that each completed feature is architecturally complete rather than partially implemented.

---

# 9. Audit Conclusions

The architectural audit reached the following conclusions:

✔ The theoretical foundation is strong.

✔ The existing architecture supports the project's long-term vision.

✔ Most remaining work concerns integration rather than invention.

✔ Existing planning abstractions should become the centre of future development.

✔ Duplication should be eliminated through consolidation rather than replacement.

✔ Progression generation should become destination-driven rather than chord-driven.

✔ Version 1 should be completed by implementing one complete reasoning pathway at a time.

These conclusions underpin every recommendation contained within the remainder of this Blueprint.

---

## Next Chapter

**Chapter 3 — The Target Architecture**

The next chapter defines the architecture toward which all remaining development will converge, establishing the layered planning model that will support the Continue, Resolve, Build Tension and Surprise Me pathways while remaining extensible for future compositional intelligence.

---

_End of Chapter 2_
