# NEPM Skill System

A kernel-like cognition skill system for interpreting nonlinear human input through structural continuity rather than surface intent alone.

This repository packages a set of interoperable skills built around:

- Continuity
- Snapshot
- Trace
- Grammar Layer v1
- RIS / Hard Stop boundary logic

The system is designed for situations where the goal is not merely to answer a question, but to determine:

- what is happening structurally
- which thread is active
- which phase the user is in
- what kind of move is being made
- whether a trap is forming
- what is actually helpful now
- whether output should continue, constrain, degrade, or stop
- how raw cognition should be translated into externally usable form

## Repository structure

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

## Design philosophy

This system does not attempt to define the ontology of cognition.

It attempts to receive cognitive movement, preserve continuity across that movement, generate snapshots where needed, detect structural risk, and translate raw thought into usable external outputs without erasing the original judgment.

## Included skills

### nepm-kernel

The core interpretive layer.

### nepm-orchestrator

A routing skill that decides which sub-skill should be activated.

### trap-detector

Detects structural, cognitive, or execution traps.

### helpful-now-deriver

Determines the smallest genuinely useful next move.

### decision-snapshot-builder

Builds a stable temporary decision surface.

### founder-thought-translator

Translates nonlinear raw thought into sendable output without betraying the original landing point.

## Intended use

This repository is useful for:

- founder cognition support
- agent orchestration
- decision support
- structured writing translation
- continuity-aware AI systems
- personal AI OS interfaces
- long-horizon human-AI interaction

## Status

Early structural version.
The current goal is not feature completeness.
The current goal is preserving the architecture clearly enough that it can be reused, tested, and evolved.

## Suggested first commit

```bash
git init
git add .
git commit -m "init nepm skill system"
```

## Suggested GitHub description

Kernel-like cognition skill system for continuity-aware interpretation, decision snapshots, trap detection, and faithful translation of nonlinear thought.

## Suggested tags

- skills
- agent
- cognition
- decision-support
- ai-os
