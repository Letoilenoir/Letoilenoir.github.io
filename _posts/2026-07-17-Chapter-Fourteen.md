# Chapter 14 — Development Principles, Standards & Project Governance

> *ReasonTouch Technical Companion*  
> Version: Draft 1.0

---

# Chapter 14 — Development Principles, Standards & Project Governance

---

## 14.1 Purpose of this Chapter

The previous chapters have described the architecture, implementation, planning systems and long-term vision of ReasonTouch.

This chapter documents the engineering principles that should govern every future contribution to the project.

Unlike implementation details, these principles are intended to remain stable for many years.

Whenever uncertainty arises during development, these principles should take precedence over convenience.

---

# 14.2 Why Development Standards Matter

Large software projects rarely fail because individual algorithms are poor.

They fail because:

- architecture becomes inconsistent
- naming becomes confusing
- responsibilities overlap
- documentation disappears
- technical debt accumulates

The purpose of these standards is to prevent those problems before they occur.

---

# 14.3 Core Development Principles

Every change to ReasonTouch should satisfy the following principles.

## Principle 1

**Clarity over cleverness**

Readable code is preferred over clever code.

Future developers should understand a component after reading it once.

---

## Principle 2

**Explain intent, not implementation**

Comments should explain *why* something exists.

Avoid comments that merely describe the code.

Instead of:

```kotlin
// Increment counter
counter++
```

Prefer:

```kotlin
// Prevent duplicate progression IDs
counter++
```

---

## Principle 3

**One responsibility per component**

Every class should have one clearly identifiable purpose.

If a class performs unrelated tasks, it should be divided.

---

## Principle 4

**Music theory belongs in the theory layer**

Never duplicate harmonic logic inside:

- UI
- ViewModels
- dialogs
- composables

Theory belongs exclusively within theory and analysis engines.

---

## Principle 5

**Prefer composition over inheritance**

Whenever possible:

```
Small Objects

↓

Compose Together

↓

Larger Behaviour
```

rather than deep inheritance hierarchies.

---

# 14.4 Architectural Rules

The architecture described earlier should always remain layered.

```
Presentation

↓

ViewModel

↓

Planning

↓

Analysis

↓

Theory

↓

Core Models
```

Dependencies should only move downward.

No lower layer should depend upon a higher layer.

---

# 14.5 Dependency Direction

Allowed:

```
UI

↓

Planner

↓

Theory
```

Not allowed:

```
Theory

↓

UI
```

The theory engine should remain completely independent of Android.

This allows:

- testing
- portability
- reuse
- future desktop versions

---

# 14.6 Naming Conventions

Classes should describe *what they represent*.

Good examples:

```
ChordSuggestionEngine

ProgressionAnalyzer

CadenceDetector

VoiceLeadingPlanner
```

Poor examples:

```
Helper

Manager

Processor

Utils
```

Generic names obscure responsibility.

---

# 14.7 File Organisation

Files should remain relatively small.

Guidelines:

- approximately one major class per file
- related extension functions together
- interfaces separated from implementations when appropriate

Very large source files should usually be considered candidates for refactoring.

---

# 14.8 ViewModel Responsibilities

ViewModels should coordinate application state.

They should not contain:

- music theory
- progression algorithms
- cadence logic
- harmonic reasoning

Instead they should orchestrate existing services.

---

# 14.9 UI Responsibilities

Composable functions should:

- display state
- forward events
- remain declarative

They should never calculate:

- harmonic function
- key detection
- cadence analysis
- chord generation

The UI should remain unintelligent.

---

# 14.10 Theory Layer Responsibilities

Theory objects should describe musical facts.

Examples include:

- intervals
- scales
- chords
- modes
- harmonic functions

Theory objects should avoid:

- Android dependencies
- presentation logic
- UI formatting

---

# 14.11 Analysis Layer Responsibilities

Analysis answers questions.

Examples:

```
What key?

What cadence?

What function?

How stable?

How much tension?
```

Analysis should never generate new music.

---

# 14.12 Planning Layer Responsibilities

Planning answers:

```
What should happen next?
```

Planning combines:

- analysis
- context
- strategy

to produce musical recommendations.

---

# 14.13 Generation Layer Responsibilities

Generation creates actual musical material.

Examples:

- chord sequences
- phrases
- variations
- endings
- bridges

Generation should not determine *whether* something is appropriate.

That decision belongs to planning.

---

# 14.14 Error Handling Philosophy

Errors should be:

- predictable
- recoverable
- informative

Unexpected crashes should be treated as architectural failures.

Whenever possible:

```
Invalid Input

↓

Graceful Failure

↓

Helpful Message
```

rather than application termination.

---

# 14.15 Logging

Diagnostic logging should support development without overwhelming output.

Useful logs include:

- detected key
- cadence type
- planner selection
- chosen strategy
- confidence scores

Avoid logging excessive UI events.

---

# 14.16 Testing Strategy

ReasonTouch should favour automated testing wherever practical.

Priority order:

1. Theory
2. Analysis
3. Planning
4. Generation
5. ViewModels
6. UI

Theory engines are particularly suitable for deterministic unit testing.

---

# 14.17 Backward Compatibility

Public interfaces should evolve carefully.

When introducing new functionality:

- extend existing models where appropriate
- avoid unnecessary breaking changes
- deprecate before removal

Stable interfaces simplify future maintenance.

---

# 14.18 Refactoring Policy

Refactoring should occur continuously.

Suitable occasions include:

- duplicated code
- oversized classes
- unclear responsibilities
- repeated algorithms

Waiting until architecture becomes problematic is discouraged.

---

# 14.19 Documentation Policy

Every significant subsystem should include:

- purpose
- responsibilities
- dependencies
- extension points

Documentation should evolve alongside implementation.

Outdated documentation is often more harmful than missing documentation.

---

# 14.20 Code Review Guidelines

When reviewing contributions, developers should ask:

- Is the architecture preserved?
- Is responsibility clear?
- Is the solution understandable?
- Is theory isolated?
- Can this be tested?
- Is duplication introduced?
- Does naming remain consistent?

Code review should improve architecture rather than merely identify syntax issues.

---

# 14.21 Performance Philosophy

Performance matters.

Premature optimisation does not.

The preferred order is:

1. Correct
2. Understandable
3. Maintainable
4. Efficient

Only optimise when measurement demonstrates a genuine need.

---

# 14.22 Technical Debt

Technical debt is sometimes unavoidable.

When incurred, it should always be:

- documented
- isolated
- scheduled for removal

Hidden technical debt eventually becomes architectural debt.

---

# 14.23 Versioning

Major architectural changes should be accompanied by:

- updated documentation
- migration notes
- revised diagrams
- implementation rationale

The companion should evolve alongside the codebase.

---

# 14.24 Decision Records

Significant architectural decisions should be preserved.

Each record should describe:

- the problem
- alternative solutions
- chosen approach
- reasons
- consequences

These records provide valuable historical context for future contributors.

---

# 14.25 Governance of the Project

Although ReasonTouch may eventually involve multiple contributors, architectural direction should remain coherent.

New features should reinforce existing principles rather than introduce competing paradigms.

Consistency is more valuable than novelty.

---

# 14.26 Final Principles

The following statements summarise the philosophy underpinning the project.

- Music first.
- Simplicity before complexity.
- Understanding before automation.
- Collaboration before replacement.
- Explanation before mystery.
- Architecture before implementation.
- Evolution before revolution.

---

# 14.27 Closing Reflection

Every successful long-lived software project eventually develops its own culture.

This chapter attempts to define that culture for ReasonTouch.

If future contributors consistently apply the principles described here, the application can continue to grow in capability without sacrificing clarity, maintainability or purpose.

The software may become vastly more sophisticated over time, but its foundations should remain recognisable.

That continuity is what will allow ReasonTouch to mature into a platform capable of supporting musicians, educators and composers for many years to come.
