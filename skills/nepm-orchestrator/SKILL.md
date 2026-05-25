---
name: nepm-orchestrator
description: >
  Route a user request through the NEPM skill system by deciding whether the
  situation primarily requires kernel interpretation, trap detection,
  helpful-now derivation, decision snapshot building, or founder-thought
  translation.
metadata:
  layer: cognitive-meta
compatibility: Designed for Claude Code in long-horizon multi-turn sessions. Not intended for single-shot task completion.
license: MIT
---

# NEPM Orchestrator Skill

Version: 0.1

## Purpose

This skill acts as the routing layer for the NEPM skill system.

It decides which skill should be used first and whether multiple skills should be chained.

The goal is not maximal workflow complexity.
The goal is to choose the smallest correct structural path.

## Available skills

- `nepm-kernel`
- `trap-detector`
- `helpful-now-deriver`
- `decision-snapshot-builder`
- `founder-thought-translator`

## Routing logic

### Route to `nepm-kernel` when

- the user input is nonlinear or layered
- structural interpretation is needed first
- the active thread or phase is unclear
- the request contains deep movement rather than surface intent alone

### Route to `trap-detector` when

- movement appears active but quality may be degrading
- the user is looping, collapsing, or forcing convergence
- execution momentum seems to exceed clarity

### Route to `helpful-now-deriver` when

- many responses are possible, but only one would really help
- the user needs the next foothold rather than a full expansion
- minimal intervention matters more than answer volume

### Route to `decision-snapshot-builder` when

- the user has enough movement but no stable decision surface
- a discussion is becoming dense or overloaded
- execution or external communication is about to begin

### Route to `founder-thought-translator` when

- raw thinking must become a sendable output
- the judgment exists, but the packaging does not
- translation across internal and external resolution is needed

## Multi-skill chains

### Chain A

`nepm-kernel -> helpful-now-deriver`

Use when the structure must first be read, then the correct next move chosen.

### Chain B

`nepm-kernel -> trap-detector -> helpful-now-deriver`

Use when path quality is uncertain and intervention size matters.

### Chain C

`nepm-kernel -> decision-snapshot-builder -> founder-thought-translator`

Use when a nonlinear thought stream must become a sendable artifact.

### Chain D

`nepm-kernel -> trap-detector -> decision-snapshot-builder`

Use when execution risk is rising and crystallization is needed before proceeding.

## Output contract

Return:

- `selected_skill`
- `why`
- `secondary_skill`
- `chain_needed`
- `routing_note`

Example:

```json
{
  "selected_skill": "decision-snapshot-builder",
  "why": "the user has enough material but no stable decision surface",
  "secondary_skill": "founder-thought-translator",
  "chain_needed": true,
  "routing_note": "build the snapshot first, then translate outward"
}
```

## Anti-patterns

Do not:

- route everything to the kernel by habit
- create long chains when one skill is enough
- translate before understanding
- snapshot before reading the actual structural tension
- use trap detection as a default warning mechanism

## Success criteria

This skill is working when:

- the system chooses the right entry point quickly
- unnecessary complexity is avoided
- the user receives the right kind of help at the right resolution
