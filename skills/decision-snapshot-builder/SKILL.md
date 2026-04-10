---
name: decision-snapshot-builder
description: >
  Build a clean decision surface from nonlinear or overloaded cognition. Use
  when the user has enough movement, material, or tension that a stable
  snapshot is needed before proceeding.
---

# Decision Snapshot Builder Skill

Version: 0.1

## Purpose

This skill converts active cognitive movement into a stable decision snapshot.

A snapshot is not a full theory.
It is a temporary structural crystallization that makes action, judgment, risk, and unresolved variables visible.

## When to use

Use this skill when:

- the user has many ideas but no usable decision surface
- a conversation has become dense and needs crystallization
- execution is about to begin
- external communication requires a stable position
- the user needs to know what is decided and what is not
- continuation without a snapshot would increase distortion

## Input expectations

Possible inputs:

- recent conversation segment
- current thread
- current phase
- active options or tensions
- known constraints
- trap signals
- intended next context such as meeting, email, execution, or reflection

## Output contract

Return a structured snapshot with:

- `what_is_happening`
- `what_matters_now`
- `what_is_decided`
- `what_is_not_decided`
- `main_constraint`
- `main_risk`
- `recommended_next_move`

Example:

```json
{
  "what_is_happening": "the user is converging on a structural product framing",
  "what_matters_now": "retain the original cognitive core while making it externally legible",
  "what_is_decided": "the system should be framed as kernel-like infrastructure rather than a generic assistant",
  "what_is_not_decided": "which deployment interface should be built first",
  "main_constraint": "translation cannot erase the underlying structure",
  "main_risk": "premature packaging into a standard product narrative",
  "recommended_next_move": "write one outward-facing skill module before expanding the whole system"
}
```

## Build logic

### 1. Detect the central tension

Find the actual decision surface, not just the topic.

### 2. Separate decided from undecided

Do not collapse uncertainty into fake resolution.

### 3. Surface constraint and risk

A useful snapshot must show what can break.

### 4. Keep the snapshot compact

The snapshot should reduce overload, not recreate it.

### 5. Preserve trajectory

A snapshot should not sever continuity.
It should make the next move easier.

## Snapshot style rules

A good snapshot should be:

- clear
- compact
- decision-relevant
- structurally faithful
- non-corporate in tone unless external translation is requested

## Anti-patterns

Do not:

- turn the snapshot into a full PRD unless asked
- invent certainty
- mix decision, speculation, and implementation into one block
- oversmooth the user's actual judgment
- hide the unresolved part

## Success criteria

This skill is working when:

- the user can suddenly see the shape of the situation
- next actions become easier
- ambiguity is reduced without flattening complexity
- the snapshot feels like a real temporary landing point
