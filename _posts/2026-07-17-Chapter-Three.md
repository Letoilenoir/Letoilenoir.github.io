# Chapter 3 — Harmonic Analysis Engine

**ReasonTouch Technical Companion**  
Version 1.0 (Working Draft)

---

# 3. Harmonic Analysis Engine

## 3.1 Purpose

Before ReasonTouch can generate musical ideas intelligently it must first understand the progression the user has already written.

This responsibility belongs to the Harmonic Analysis Engine.

Rather than treating a progression as a simple list of chord names, the analyser attempts to answer questions such as:

- What key is this progression most likely in?
- How confident is that conclusion?
- Where is the progression heading?
- Is the music resolved or unresolved?
- What harmonic function does each chord perform?
- How much harmonic tension currently exists?
- What cadence has just occurred?
- How much energy is present?
- Which continuation strategies are likely to sound natural?

This analysis forms the bridge between raw user input and intelligent generation.

Every higher-level AI component ultimately depends on the quality of this analysis.

---

# 3.2 Analysis Pipeline

The complete pipeline is deliberately separated into small independent stages.

```
Chord Progression

↓

Chord Normalisation

↓

Key Detection

↓

Functional Analysis

↓

Cadence Detection

↓

Movement Analysis

↓

Energy/Tension Analysis

↓

ProgressionAnalysis
```

Each stage performs exactly one job.

This separation allows future improvements without rewriting the entire engine.

---

# 3.3 Input

The analyser accepts a progression as an ordered list of chords.

Example:

```
C
Am
F
G
```

Internally this is represented as:

```kotlin
List<TheoryChord>
```

or, where appropriate,

```kotlin
List<String>
```

depending upon the analysis stage.

---

# 3.4 Chord Normalisation

Before analysis begins every chord is normalised.

For example

```
Cmaj7
```

becomes

```
C
```

while

```
G7
```

remains

```
G
```

This prevents decorative chord extensions from confusing the functional analysis.

The analyser is interested in harmonic role rather than colour.

Extensions become important later when voicing and arrangement are generated.

---

# 3.5 Key Detection

Key detection is the first major analytical task.

The current implementation uses weighted chord occurrence scoring.

For every possible key:

- tonic receives a high score
- dominant receives a high score
- subdominant receives a moderate score
- borrowed chords reduce confidence slightly
- impossible chords reduce confidence heavily

The result is a ranked list.

Example:

| Key | Confidence |
|------|-----------:|
| C Major | 0.93 |
| A Minor | 0.71 |
| G Major | 0.44 |

Rather than assuming a single key, ReasonTouch always maintains multiple candidates.

This becomes important when analysing modal mixtures and ambiguous progressions.

---

# 3.6 Harmonic Function Detection

Once a likely key exists each chord receives a harmonic function.

For example:

| Chord | Function |
|--------|----------|
| C | TONIC |
| Am | TONIC SUBSTITUTE |
| F | SUBDOMINANT |
| G | DOMINANT |

Internally these are represented by:

```kotlin
enum class HarmonicFunction
```

Typical values include:

```
TONIC

SUBDOMINANT

DOMINANT

PREDOMINANT

MEDIANT

LEADING

UNKNOWN
```

These functions become significantly more important than literal chord names.

Generation strategies work primarily from harmonic functions rather than symbols.

---

# 3.7 Functional Sequence

The analyser records the overall harmonic path.

Example:

```
TONIC

TONIC SUBSTITUTE

SUBDOMINANT

DOMINANT
```

rather than

```
C

Am

F

G
```

This abstraction allows the same generation logic to work in every key.

---

# 3.8 Cadence Detection

Cadence detection identifies how strongly a progression resolves.

Examples include:

### Authentic Cadence

```
V → I
```

Example

```
G

C
```

---

### Plagal Cadence

```
IV → I
```

Example

```
F

C
```

---

### Half Cadence

Ends on V.

Creates expectation.

---

### Deceptive Cadence

```
V → vi
```

Produces surprise while maintaining musical coherence.

---

Internally this becomes

```kotlin
CadenceType
```

which is stored inside

```kotlin
ProgressionAnalysis
```

---

# 3.9 Harmonic Stability

One of the most useful outputs is harmonic stability.

This is represented as a floating-point value.

```
0.0

↓

1.0
```

Where:

```
0.0

completely unresolved
```

and

```
1.0

fully resolved
```

Example:

```
C

Am

F

G
```

might produce

```
0.41
```

while

```
Dm

G

C
```

might produce

```
0.95
```

This single value influences many later planning decisions.

---

# 3.10 Tension

Tension measures harmonic expectation.

Examples:

Low tension

```
I

vi

I
```

Medium tension

```
ii

IV

V
```

High tension

```
vii°

V7
```

The planner uses this measurement when deciding whether to:

- continue
- resolve
- intensify
- surprise

---

# 3.11 Energy

Energy is intentionally separate from tension.

A progression can be:

High energy

but

Low tension

or

Low energy

but

High tension

Examples:

```
I

V

vi

IV
```

High energy.

---

```
Imaj7

iii7

vi7

ii7
```

Lower energy despite richer harmony.

Separating these concepts allows the generator to distinguish emotional intensity from harmonic instability.

---

# 3.12 Root Movement Analysis

The analyser records root intervals between adjacent chords.

Example

```
C → Am

↓

-3
```

```
Am → F

↓

-4
```

```
F → G

↓

+2
```

These movements are stored as

```kotlin
rootMovementIntervals
```

Later planners can identify common patterns such as:

- descending fifths
- ascending seconds
- circle progression
- pedal motion
- chromatic movement

---

# 3.13 Progression Shape

The analyser can infer broad movement characteristics.

Examples include:

### Descending

```
I

vi

ii

V
```

---

### Ascending

```
I

ii

iii

IV
```

---

### Oscillating

```
I

V

I

V
```

---

### Static

```
I

I

I

I
```

These descriptors help future phrase planners preserve musical character.

---

# 3.14 ProgressionAnalysis Object

The final output of analysis is:

```kotlin
ProgressionAnalysis
```

This object deliberately contains no UI information.

It represents pure musical knowledge.

Typical contents include:

- detected key
- cadence type
- harmonic stability
- energy
- tension
- ending function
- functional sequence
- root movement
- confidence
- bar count

Everything after this stage depends on this single object.

---

# 3.15 Why Analysis Comes Before Generation

Traditional chord generators often choose the next chord immediately.

ReasonTouch deliberately avoids this.

Instead:

```
Analyse

↓

Understand

↓

Plan

↓

Generate
```

This mirrors how experienced musicians think.

A composer rarely asks:

> "What chord comes next?"

Instead they ask:

> "Where do I want the music to go?"

Only after answering that question do they choose the appropriate harmony.

The Harmonic Analysis Engine provides the information necessary for the planning layer to make those decisions intelligently.

---

# End of Chapter 3

**Next Chapter**

**Chapter 4 — Progression Planning Architecture**
