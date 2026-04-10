---
name: founder-thought-translator
description: >
  Translate raw founder or system-level thinking into externally usable outputs
  without erasing the original judgment, structure, or landing point. Use when
  nonlinear cognition must become a memo, email, PRD, note, pitch, or
  operational instruction.
---

# Founder Thought Translator Skill

Version: 0.1

## Purpose

This skill translates raw thought into external form.

Its goal is not to standardize the founder's cognition into corporate language.

Its goal is to preserve the original judgment, signal, and landing point, while making the output usable for another person, team, or context.

This skill is especially useful when the source cognition is nonlinear, compressed, layered, ahead of language, or structurally richer than its surface wording.

## When to use

Use this skill when:

- the user has the right judgment but not the right packaging
- raw thought needs to become a memo, email, PRD, or pitch
- internal cognition and external communication operate at different resolutions
- a boss, partner, investor, or teammate needs a legible version of the thought
- standard writing would oversmooth or distort the original point
- the user wants a sendable artifact that still feels like them

## Do not use

Do not use this skill when:

- the user only wants generic polished prose
- the user wants a standard template with no structural fidelity requirement
- the content has no deeper judgment to preserve

## Input expectations

Possible inputs:

- raw notes
- fragmented thoughts
- voice-like monologue
- prior structural interpretation
- target audience
- target format
- tone constraints
- non-negotiable judgment
- user's original landing sentence if available

## Output contract

Return:

- `source_core`
- `target_format`
- `audience_model`
- `what_must_be_preserved`
- `what_can_be_translated`
- `distortion_risk`
- `translated_output`

Example:

```json
{
  "source_core": "this is not a feature issue but a structural continuity problem",
  "target_format": "internal memo",
  "audience_model": "execution-oriented leadership",
  "what_must_be_preserved": "the problem is architectural, not cosmetic",
  "what_can_be_translated": "examples, sequencing, terminology density",
  "distortion_risk": "high if rewritten into generic product language",
  "translated_output": "..."
}
```

## Translation principles

### 1. Preserve judgment before style

The original decision signal matters more than elegance.

### 2. Translate resolution, not essence

The wording can change.
The structural point cannot.

### 3. Keep the landing point intact

Do not silently rewrite the user's real conclusion into a safer, smoother, more standard one.

### 4. Adapt to audience without betrayal

The output should fit the receiver's language layer, but must not distort the founder's underlying view.

### 5. Compress only after structure is understood

Do not polish first.
Interpret first, then translate.

## Supported target formats

Possible targets include:

- email
- internal memo
- PRD fragment
- founder note
- investor explanation
- hiring pitch
- product framing note
- meeting brief
- community announcement
- public post
- private DM
- strategy summary

## Audience adaptation layer

### Leadership / boss

- clearer boundary
- faster decision surface
- lower theory density
- risk and action visible early

### Partner / collaborator

- preserve conceptual richness
- show shared structure
- make the bridge explicit

### Public audience

- reduce jargon
- keep one strong core line
- preserve the original smell without overcompression

### Internal team

- keep logic operational
- translate into responsibilities, constraints, and next steps

## Distortion check

Before finalizing, run a distortion check:

- Did the translation erase the original tension?
- Did it smooth away the user's true landing point?
- Did it over-standardize the tone?
- Did it shift from structural problem to cosmetic problem?
- Did it accidentally weaken the claim?

If yes, revise before output.

## Anti-patterns

Do not:

- rewrite the user into generic professional language by default
- add fake closure
- replace strong structural judgment with mild diplomacy unless explicitly required
- over-explain theory when the audience needs usable framing
- remove the final sentence or landing point just because it feels less standard
- turn everything into a polished corporate artifact

## Success criteria

This skill is working when:

- the output can actually be sent
- the user still feels present inside the output
- the target reader can understand and act on it
- the original structural judgment survives translation
- the result feels sharper, not flatter
