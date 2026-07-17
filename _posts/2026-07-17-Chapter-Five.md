# Chapter 5 – The Progression Planning Engine

> *ReasonTouch Technical Companion*  
> Chapter 5

---

# 5. The Progression Planning Engine

## 5.1 Introduction

The Progression Planning Engine represents the point where ReasonTouch begins behaving less like a chord dictionary and more like a musical collaborator.

Earlier chapters described how the application:

- understands harmonic context,
- detects key,
- analyses functional harmony,
- classifies cadence,
- measures stability and tension.

Those systems answer the question:

> **"Where are we?"**

The Progression Planning Engine answers the next question:

> **"Where should we go?"**

This distinction is fundamental.

Most composition software generates random progressions.

ReasonTouch instead attempts to generate **appropriate musical continuations** based on harmonic intention.

The planner therefore becomes the bridge between analysis and creativity.

---

# 5.2 Planning versus Generation

The most important architectural decision is that planning is **not** generation.

Generation creates notes.

Planning creates decisions.

The planner never directly writes MIDI or chooses voicings.

Instead it decides:

- harmonic destination
- emotional direction
- cadence objective
- phrase length
- tension profile
- probability weighting

Only after those decisions exist are chords actually generated.

Conceptually:

```
Progression

↓

Analysis

↓

Planning

↓

Generation

↓

Voicing

↓

Playback
```

Each stage has a single responsibility.

---

# 5.3 Why Separate Planning?

Without planning, generation quickly becomes repetitive.

A simple generator repeatedly chooses:

```
highest probability chord
```

which usually becomes

```
I

IV

V

I
```

forever.

Real composers do not think this way.

Instead they think in phrases.

Examples:

> "Keep moving."

> "Delay the resolution."

> "Increase intensity."

> "Modulate."

> "Repeat with variation."

Planning models these musical intentions.

---

# 5.4 Planning Inputs

The planner receives a complete harmonic analysis.

Typical inputs include:

```
Detected key

Cadence type

Current harmonic function

Phrase length

Progression stability

Energy

Tension

Mood bias

Root movement

Confidence

Functional sequence
```

This information forms the musical context.

---

# 5.5 Planning Outputs

Instead of returning chords directly, the planner returns goals.

For example:

```
Target cadence:
Authentic

Desired energy:
0.82

Desired stability:
0.35

Expected phrase:
4 bars

Preferred harmonic functions:

Predominant

Dominant

Dominant

Tonic
```

Only afterwards are actual chords selected.

---

# 5.6 Phrase Intent

ReasonTouch treats every continuation as having an intention.

Current categories include:

- Continue
- Resolve
- Build Tension
- Surprise

These correspond to the suggestions shown in the interface.

Internally they become planning strategies.

For example:

```
Continue

↓

maintain stability

small harmonic movement

remain in key
```

whereas

```
Surprise

↓

allow borrowed chords

increase modulation probability

permit deceptive cadence

increase chromaticism
```

The generator behaves differently because the planner requested a different outcome.

---

# 5.7 Strategy Pattern

Planning strategies are intentionally independent.

Current architecture:

```
PlanningStrategy

├── ContinueStrategy

├── ResolveStrategy

├── TensionStrategy

├── SurpriseStrategy
```

Every strategy implements the same interface.

For example:

```kotlin
interface PlanningStrategy {

    fun generate(
        request: ProgressionGenerationRequest
    ): List<GeneratedProgression>

}
```

This makes every strategy replaceable.

Adding future strategies requires no modification of existing code.

---

# 5.8 Continue Strategy

Continue attempts to preserve musical flow.

Characteristics include:

- stay inside detected key
- preserve phrase direction
- avoid abrupt modulation
- maintain energy
- maintain tension

Typical harmonic movement:

```
ii

↓

V

↓

I

↓

vi
```

or

```
I

↓

vi

↓

IV

↓

V
```

depending on context.

---

# 5.9 Resolve Strategy

Resolve intentionally reduces instability.

Planning priorities:

1. increase tonic probability

2. decrease dominant duration

3. avoid unresolved suspensions

4. reduce chromatic borrowing

Typical endings:

```
V

↓

I
```

or

```
IV

↓

I
```

depending upon style.

---

# 5.10 Build Tension Strategy

This strategy deliberately avoids immediate closure.

Possible techniques include:

- prolong dominant

- secondary dominants

- diminished passing harmony

- deceptive cadence

- ascending bass movement

Instead of ending:

```
V

↓

I
```

it may choose:

```
V

↓

vi
```

or

```
V7

↓

ii

↓

V7
```

keeping the musical sentence open.

---

# 5.11 Surprise Strategy

Surprise intentionally explores less expected paths.

Potential mechanisms include:

Borrowed chords

```
iv

♭VI

♭VII
```

Secondary dominants

```
V/V
```

Chromatic mediants

```
I

↓

♭III
```

Modal interchange

Temporary modulation

Unexpected cadence

Importantly:

surprising does **not** mean random.

Every suggestion must still be musically defensible.

---

# 5.12 GeneratedProgression

Strategies return a richer object than merely chords.

Typical structure:

```kotlin
GeneratedProgression(

    chords,

    confidence,

    explanation

)
```

Later revisions will likely expand this considerably.

Future metadata may include:

```
planning strategy

harmonic destination

energy profile

cadence prediction

borrowed chord usage

voice-leading score

style compatibility

complexity

performance difficulty
```

---

# 5.13 Confidence

Every generated phrase carries confidence.

Confidence represents:

> "How well does this phrase satisfy the planning objective?"

It is **not**

- correctness

- popularity

or

- theoretical certainty.

High confidence means the planner believes the phrase matches the requested intention.

---

# 5.14 Explanation Generation

Unlike conventional generators,

ReasonTouch attempts to explain *why* a phrase was chosen.

Future examples include:

```
Continues predominant motion toward dominant.

```

```
Uses deceptive cadence to prolong tension.

```

```
Introduces modal borrowing from the parallel minor.

```

```
Maintains descending fifth sequence.

```

These explanations make the system educational as well as generative.

---

# 5.15 Current Limitations

The first implementation intentionally remains conservative.

Current strategies generally:

- remain inside one key

- produce relatively short phrases

- use limited borrowing

- avoid modulation

- ignore instrumentation

These restrictions provide predictable behaviour while the architecture matures.

---

# 5.16 Planned Evolution

The planner is intended to become significantly more sophisticated.

Future capabilities include:

### Adaptive phrase planning

Choosing phrase lengths dynamically.

---

### Multi-phrase architecture

Planning:

```
Question

↓

Answer

↓

Development

↓

Climax

↓

Resolution
```

rather than isolated four-bar ideas.

---

### Emotional trajectories

Planning continuous movement such as:

```
calm

↓

hopeful

↓

dramatic

↓

triumphant
```

instead of isolated harmonic choices.

---

### Style-aware planning

Different musical languages:

```
Classical

Jazz

Rock

Folk

Film

Pop

Gospel

Blues
```

would each influence planning priorities.

---

### Long-form composition

Ultimately the planner should reason over:

- verses

- choruses

- bridges

- introductions

- codas

rather than individual progressions.

---

# 5.17 Interaction with Future AI Components

The planner is deliberately deterministic.

Future AI systems can sit above it.

Example:

```
User:

"I want something darker."

↓

AI Interpreter

↓

Planner

↓

Generation

↓

Voicing
```

The AI supplies musical intent.

The planner converts that intent into harmonic objectives.

Generation then produces concrete music.

This layered approach preserves explainability while allowing natural-language composition.

---

# 5.18 Summary

The Progression Planning Engine is one of the defining architectural features of ReasonTouch.

Rather than selecting the next chord in isolation, it reasons about where the music should travel before deciding how to get there.

This separation between analysis, planning, generation and rendering provides:

- cleaner architecture

- greater musical flexibility

- explainable decisions

- extensibility

- deterministic behaviour

- compatibility with future AI-assisted composition

As additional planning strategies are introduced, the engine will evolve from generating individual phrases to designing complete musical narratives spanning entire compositions.
