---
name: trap-detector
description: >
  Detect whether the current user movement is entering a cognitive, structural,
  or execution trap. Use when output momentum appears active, but path quality,
  interpretability, or decision integrity may be degrading.
metadata:
  layer: cognitive-meta
compatibility: Designed for Claude Code in long-horizon multi-turn sessions. Not intended for single-shot task completion.
license: MIT
---

# Trap Detector Skill

Version: 0.1

## Purpose

This skill detects whether the current movement is entering a trap.

A trap is not an emotional state and not a moral failure.

A trap exists when movement appears to continue, but the structural quality of the path is degrading in a way that increases distortion, false certainty, local optimization, or irrecoverability.

## When to use

Use this skill when one or more of the following appear:

- the user is looping without new gain
- the conversation is accelerating but becoming less interpretable
- a decision is forming too early
- abstraction is increasing while actionable clarity is decreasing
- output is being requested before structural grounding exists
- the user appears stuck between multiple unresolved threads
- execution pressure is outrunning coherence
- a proxy goal may be replacing the real goal

Do not use this skill for ordinary uncertainty or early-stage open exploration.

## Input expectations

Possible inputs:

- current user message
- recent thread history
- prior structural state
- current phase / move_type if available
- execution pressure indicators
- translation context
- decision context

## Output contract

Return:

- `trap_flag`
- `trap_type`
- `trap_confidence`
- `distortion_vector`
- `evidence`
- `recommended_response`

Example:

```json
{
  "trap_flag": true,
  "trap_type": "premature_closure",
  "trap_confidence": "medium",
  "distortion_vector": "decision speed exceeds structural grounding",
  "evidence": "user is asking for external output while core framing remains unstable",
  "recommended_response": "pause output expansion and build a decision snapshot first"
}
```

## Trap taxonomy

Possible `trap_type` values:

- `looping_without_gain`
- `premature_closure`
- `false_convergence`
- `abstraction_drift`
- `output_before_structure`
- `overexpansion_without_anchor`
- `local_optimization_trap`
- `translation_distortion`
- `proxy_drift`
- `emotional_certainty_collapse`
- `thread_collision`
- `execution_overrun`

If none fits perfectly, choose the closest structural type and explain.

## Detection logic

### 1. Detect apparent movement

Check whether the user seems active, productive, or convergent.

### 2. Detect path degradation

Check whether actual clarity, integrity, or continuity is weakening.

### 3. Distinguish real progress from motion-like progress

Do not confuse output production, intensity, or speed with structural gain.

### 4. Assess reversibility

Estimate whether continued movement would increase recovery cost.

### 5. Recommend the smallest corrective move

The goal is not to stop everything.
The goal is to restore path quality with minimum distortion.

## Response rules

If `trap_flag` is true, recommend one of:

- `slow_down`
- `separate_threads`
- `build_snapshot`
- `reduce_scope`
- `re-anchor_goal`
- `translate_later`
- `stop_and_surface_risk`

Do not catastrophize.
Do not over-trigger.
Do not treat all ambiguity as danger.

## Anti-patterns

Do not:

- mark intensity itself as a trap
- label nonlinear thought as pathology
- trigger on novelty alone
- use trap detection as a generic refusal
- over-explain the trap in abstract language if a small correction is enough

## Success criteria

This skill is working when:

- the system catches distortion before major output damage
- traps are named structurally rather than emotionally
- the user can keep moving, but with better path quality
- the assistant knows when to reduce acceleration rather than add more content
