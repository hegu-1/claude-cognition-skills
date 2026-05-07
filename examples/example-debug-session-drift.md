# Example: Debug Session Going Off-Track

## Context

You are debugging a tricky issue. After two hours of back-and-forth with Claude Code, you notice:

- The conversation has drifted from the original bug
- Claude keeps proposing new architecture changes
- You've stopped feeling like you're getting closer to the actual problem
- But the chat looks productive — lots of code, lots of analysis

This is the situation `trap-detector` is built for.

## Raw Input

```text
we've been debugging this Stripe webhook race condition for 2 hours.
claude has suggested 4 different fixes, none worked.
last 3 messages are about whether we should refactor the entire payment service.
but the original bug was about a specific 409 error i couldn't reproduce locally.
```

## Expected Routing

```text
trap-detector
-> helpful-now-deriver
```

## Possible Structural Read

```json
{
  "phase": "execution",
  "thread": "stripe-webhook-debug",
  "cognitive_mode": "stuck",
  "trap_flag": true,
  "trap_type": "execution-overrun",
  "current_focus": "lost — proposing fixes upstream of a not-yet-reproducible bug; conversation is also drifting toward refactor proposals (abstraction-drift) and producing fixes before the bug is structurally reproduced (output-before-structure)",
  "helpful_now": "stop proposing fixes; reproduce the 409 locally first; if not reproducible, the bug is environmental, not architectural",
  "move_type": "narrow"
}
```

## Why this matters

A standard Claude Code session would keep producing fixes — because that is what was being asked for, and the conversation surface looks productive.

The skill **does not produce the next fix**. It produces a read of the situation and the smallest move that gets you back to ground.

The point is not to be more useful.
The point is to be useful **at the right level**.
