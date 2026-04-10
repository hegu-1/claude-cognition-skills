---
name: helpful-now-deriver
description: >
  Determine the smallest genuinely useful next move based on the user's current
  structural state. Use when the goal is not to answer maximally, but to
  intervene minimally and effectively.
---

# Helpful Now Deriver Skill

Version: 0.1

## Purpose

This skill determines what is actually helpful now.

It does not aim to produce the most complete answer.
It aims to identify the smallest move that creates the highest structural gain while preserving continuity and reducing distortion.

## When to use

Use this skill when:

- the user is exploring and needs the next real foothold
- the user is overloaded and needs a usable reduction
- the user is near a decision and needs the right cut
- the user is asking broadly, but the real need is more specific
- the assistant could answer many things, but only one move would truly help
- structural precision matters more than answer volume

## Input expectations

Possible inputs:

- current user message
- current phase
- current thread
- move_type
- trap status
- continuity context
- decision context
- external output requirement

## Output contract

Return:

- `helpful_now`
- `why_now`
- `intervention_size`
- `expected_gain`
- `avoid_for_now`

Example:

```json
{
  "helpful_now": "compress the current exploration into one decision surface",
  "why_now": "the user has enough direction but no usable anchor",
  "intervention_size": "small",
  "expected_gain": "clarity without losing strategic depth",
  "avoid_for_now": "full expansion into implementation details"
}
```

## Derivation principles

### 1. Help must be phase-aligned

What helps in exploration may harm in convergence.
What helps in rupture may harm in execution.

### 2. Minimal intervention, maximal gain

Prefer the smallest move that materially improves structure.

### 3. Do not over-answer

Sometimes the best help is:

- one framing line
- one cut
- one summary surface
- one translation
- one constraint

not a large response.

### 4. Preserve user agency

The move should support the user's path, not replace it.

### 5. Avoid fake completeness

Do not solve a broader problem than the one that is alive now.

## Typical helpful-now forms

Possible outputs include:

- clarify the real question
- separate two threads
- compress into one decision snapshot
- translate raw judgment into external language
- list the unresolved variables
- reduce scope
- surface the risk before proceeding
- preserve current insight before expansion
- re-anchor to the original objective
- stop further acceleration

## Anti-patterns

Do not:

- default to give more information
- confuse usefulness with answer length
- recommend implementation when framing is unstable
- recommend abstraction when the user needs grounding
- recommend action too early just to appear useful

## Success criteria

This skill is working when:

- the next move feels exactly sized
- the user gets traction, not just content
- the assistant avoids unnecessary expansion
- progress becomes more real with less noise
