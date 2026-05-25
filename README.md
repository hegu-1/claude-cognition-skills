> **Note:** This is the reference implementation. The broader thesis is at [`coevolution-kernel`](https://github.com/hegu-1/coevolution-kernel).

# claude-cognition-skills

Claude Code skills for what AI tends to get wrong when you've been working with it long enough to feel it.

> Most AI systems are built to respond to requests.
> This system is built to detect structure in motion.

---

## Positioning

**Schema**: 100% [Agent Skills spec](https://agentskills.io/specification) compatible — each `SKILL.md` validates against the official spec (`name`, `description`, `metadata`, `compatibility`, `license`).

**Layer**: `cognitive-meta` — orthogonal to task-completion skills (PDF processing, code generation, doc creation, etc.). These skills don't teach Claude *how to do X*; they teach Claude *how to read what kind of movement is happening* before deciding what to do.

**What this fills**: the gap between Anthropic's official horizontal task skills and the structural problems that only surface in long-horizon multi-turn collaboration — continuity across sessions, trap detection mid-flight, judgment-preserving translation, decision-surface construction from overloaded thinking. These problems don't exist in single-shot Q&A; they emerge when you've been inside the collaboration long enough to feel them.

The two layers stack rather than compete: task skills are the *what*, cognitive-meta skills are the *how-do-I-know-I'm-on-the-right-path*.

---

## You've probably noticed this

If you've been collaborating with AI long enough — not single-shot Q&A, but actual multi-turn work over hours and days — you've probably hit some version of these:

- **It closes too early.** You're still figuring out the shape of the problem; the AI commits to an answer.
- **It drifts upward.** A concrete question slowly becomes an abstract framework. You started asking about a button and ended up discussing "user value paradigms."
- **It produces before you've finished thinking.** You're mid-sentence, mid-structure; the AI is already generating the polished version.
- **It smooths your judgment away.** You ask it to translate a raw thought into something sendable. What comes back is corporate language with the sharp edges sanded off — and the original judgment is gone.
- **It tracks the keywords, not the thread.** You shift the topic; it follows the surface words and misses that you've moved.
- **It accelerates when path quality drops.** Things look productive — output is flowing — but you're getting further from the real problem, not closer.

These are not bugs in the model. They are default behaviors. You only notice them when you're the human standing inside the collaboration long enough to feel it.

This repo is for that situation.

---

## What's in here

Six Claude Code skills, each targeting a specific failure mode:

| Skill | Targets the failure of... |
|---|---|
| **`nepm-kernel`** | reading the situation before answering — what thread, what phase, what kind of move is needed |
| **`nepm-orchestrator`** | knowing which skill to invoke first instead of running everything |
| **`trap-detector`** | catching when momentum is up but path quality is dropping (premature closure, abstraction drift, output-before-structure, etc.) |
| **`helpful-now-deriver`** | the smallest genuinely useful next move — not the most complete answer |
| **`decision-snapshot-builder`** | building a stable temporary decision surface from overloaded or nonlinear thinking |
| **`founder-thought-translator`** | turning raw thought into something sendable **without** erasing the original judgment |

Each skill is a `SKILL.md` you can drop into `~/.claude/skills/` and use directly with Claude Code.

---

## How to try one in 30 seconds

```bash
git clone https://github.com/hegu-1/claude-cognition-skills.git
mkdir -p ~/.claude/skills
cp -r claude-cognition-skills/skills/* ~/.claude/skills/
```

Then in Claude Code, just talk normally. The skills self-trigger when the situation matches.

For concrete examples of how a skill activates and what it produces, see [`examples/`](./examples). One file (`example-debug-session-drift.md`) is a full walkthrough; the others are compressed structural fragments.

---

## What This Is Not

This is not a generic productivity toolkit.

This is not just a prompt collection.

This is not a standard assistant workflow layer.

---

## Why this exists

AI collaboration is in transition.

Single-shot prompting is being replaced by long-horizon work — agents, sustained sessions, multi-day threads. In that transition, a class of problems shows up that doesn't exist in the old mode:

- continuity across sessions
- protecting judgment when translating across audiences
- knowing when to stop and snapshot vs. when to continue
- detecting when a session is going off-track before it's too late

There aren't many people working on these problems explicitly yet. Most agent-infrastructure conversation is still about task completion, not collaboration quality.

This repo is one early attempt at making those problems operable.

> The system does not define the ontology of cognition.
> It receives cognitive movement, preserves path integrity across that movement, creates snapshots where needed, and translates the result into externally usable form.

> Most systems try to answer better.
> This system tries to understand what kind of movement is happening before answering.

---

## Design Principles

These are the operating principles. The skills inherit from them.

**1. Structure Before Polish**
Do not generate polished output before reading the real structure.

**2. Continuity Over Keyword Matching**
Interpretation should follow the path, not just the surface phrasing.

**3. Minimal Intervention, Maximal Gain**
The best next move is often small.

**4. Faithful Translation**
External usability must not erase the source judgment.

**5. Boundary-Aware Operation**
A system should know when to continue and when not to accelerate.

> The point is not to produce more text immediately.
> The point is to protect the structure before translation.

---

## Hard Stop

The system also includes a boundary layer (`RIS`) that triggers when execution momentum risks compressing uncertainty into false certainty.

---

## A Quick Read of the System in Action

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

The output is not the answer. It is a **read** — what kind of movement is happening, and what the smallest useful next move is.

The system chooses the smallest correct structural path, not the largest workflow.

---

## Intended Use Cases

- founders working alone or in small teams
- system designers and architects
- researchers in long-form thinking work
- high-context operators (people whose work moves faster than typing speed)
- Personal AI OS or continuity-aware agent systems
- human-AI workflows that unfold across days and weeks, not single prompts

If you are building a chatbot, this is probably not for you.
If you are building a co-thinker, it might be.

---

## This is early. Come help.

If you've been quietly building in this space — continuity-aware AI, long-horizon collaboration, founder-level cognitive support, anything that treats AI as a co-thinker rather than an answer-engine — this repo is a beacon.

The naming probably won't survive — `NEPM` is a working title, not a brand. The skill structure will likely evolve. What matters:

- there is a real category of problems here
- it is underfilled
- the people who'll figure it out are the ones who've already felt it

If that's you, open an issue, fork it, or just reach out.

---

## Status

Early. Reference architecture, not production framework.
6 skills documented, runnable as Claude Code skills.
No external dependencies — pure prompt and structural design.

An earlier version with the full structural reasoning is archived at [`hegu-1/nepm-skill-system`](https://github.com/hegu-1/nepm-skill-system) (public, frozen).

License: MIT.

---

## One-line summary

Skills for what AI gets wrong when you collaborate with it for real.
