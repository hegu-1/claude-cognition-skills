# NEPM Skill System

A kernel-like cognition skill system for continuity-aware interpretation, structural decision support, trap detection, and faithful translation of nonlinear thought.

> Most AI systems are built to respond to requests.  
> This system is built to detect structure in motion.

## What This Is

Most AI skills today are built to do tasks.

This repository is built to read movement.

It is designed for cases where surface intent is not enough, and where the real problem is hidden in structure:

- multiple threads colliding at once
- nonlinear thought that is ahead of language
- decisions forming without a stable surface
- output being requested before structure is clear
- translation that risks erasing the original judgment
- momentum increasing while path quality decreases

This system treats those situations not as noise, but as the actual operating environment.

## What Makes This Different

This is not a generic productivity toolkit.

This is not just a prompt collection.

This is not a standard assistant workflow layer.

The NEPM Skill System is a structural interface layer for cognition in motion.

Its goal is not to define cognition itself.

Its goal is to:

- preserve continuity across movement
- identify the active thread and phase
- detect structural traps before distortion hardens
- generate decision snapshots when needed
- translate raw thought into usable external form without betraying its core judgment
- know when to continue, constrain, degrade, or stop

In other words:

Most systems try to answer better.  
This system tries to understand what kind of movement is happening before answering.

## Core Orientation

The system does not define the ontology of cognition.

It receives cognitive movement, preserves path integrity across that movement, creates snapshots where needed, and translates the result into externally usable form.

That makes it especially relevant for:

- founders
- researchers
- system designers
- high-context operators
- human-AI workflows that unfold across time rather than in one-shot prompts
- Personal AI OS or continuity-aware agent systems

## Included Skills

### `nepm-kernel`

The main interpretive layer.

Used when the goal is not merely to answer a request, but to determine what is happening structurally: thread, phase, move type, trap risk, helpful next move, and whether translation or boundary control is needed.

### `nepm-orchestrator`

The routing layer.

Decides which skill should be invoked first and whether multiple skills should be chained.

### `trap-detector`

Detects when movement appears active but path quality is degrading.

This includes premature closure, abstraction drift, thread collision, output-before-structure, proxy drift, and execution overrun.

### `helpful-now-deriver`

Determines the smallest genuinely useful next move.

Not the most complete answer.  
Not the longest answer.  
The right-sized intervention now.

### `decision-snapshot-builder`

Builds a stable temporary decision surface from nonlinear or overloaded cognition.

It makes visible:

- what is happening
- what matters now
- what is decided
- what is not decided
- what risk is present
- what next move follows

### `founder-thought-translator`

Translates raw founder or system-level thinking into a sendable artifact.

Its role is not to smooth thought into corporate language.
Its role is to preserve the original judgment while making it usable for another person, team, or context.

## Quick Example

Raw input:

```text
We are not dealing with a feature packaging problem.
The issue is that the whole thing is being mistaken for a surface UX issue,
when actually the missing layer is continuity.
If we keep describing it as a smarter assistant, we will lose the real point.
```

Possible routing:

```text
nepm-kernel
-> decision-snapshot-builder
-> founder-thought-translator
```

Possible structural read:

```json
{
  "phase": "framing",
  "thread": "system-design",
  "cognitive_mode": "compressive",
  "current_focus": "preserve the continuity-layer framing before external packaging",
  "move_type": "protect",
  "trap_flag": true,
  "trap_type": "external-translation-distortion",
  "helpful_now": "build a decision snapshot before writing the outward-facing version",
  "snapshot_needed": true,
  "translation_needed": true
}
```

The point is not to produce more text immediately.
The point is to protect the structure before translation.

## Example Operating Logic

A nonlinear founder fragment may pass through:

```text
nepm-kernel
-> decision-snapshot-builder
-> founder-thought-translator
```

A structurally unstable execution moment may pass through:

```text
nepm-kernel
-> trap-detector
-> helpful-now-deriver
```

This system is designed to choose the smallest correct structural path, not the largest workflow.

## Why This Exists

There is a gap between:

- raw cognition and external language
- nonlinear thought and standard interfaces
- continuity across time and one-shot task systems
- decision tension and sendable output
- active movement and structural readability

This repository exists to make that gap operable.

## Design Principles

### 1. Structure Before Polish

Do not generate polished output before reading the real structure.

### 2. Continuity Over Keyword Matching

Interpretation should follow the path, not just the surface phrasing.

### 3. Minimal Intervention, Maximal Gain

The best next move is often small.

### 4. Faithful Translation

External usability must not erase the source judgment.

### 5. Boundary-Aware Operation

A system should know when to continue and when not to accelerate.

## Repository Structure

```text
nepm-skill-system/
  README.md
  LICENSE
  .gitignore
  skills/
    nepm-kernel/
      SKILL.md
    nepm-orchestrator/
      SKILL.md
    trap-detector/
      SKILL.md
    helpful-now-deriver/
      SKILL.md
    decision-snapshot-builder/
      SKILL.md
    founder-thought-translator/
      SKILL.md
  examples/
    example-founder-fragment.md
    example-decision-overload.md
    example-translation-case.md
```

## Intended Use Cases

- founder support
- strategic writing
- continuity-aware AI interfaces
- decision support under overload
- personal AI OS architecture
- human-AI collaboration over long horizons
- interpretive layers for agent systems
- cognitive infrastructure experiments

## Current Status

Early structural version.

The goal at this stage is not completeness.

The goal is to preserve the architecture clearly enough that it can be reused, tested, extended, and eventually deployed as a real skill system.

## One-Line Summary

A skill system for reading cognitive structure before producing output.

## Repository Metadata

Suggested GitHub description:

```text
A kernel-like cognition skill system for continuity-aware interpretation, structural decision support, trap detection, and faithful translation of nonlinear thought.
```

Suggested tags:

```text
skills
agent
cognition
decision-support
ai-os
```
