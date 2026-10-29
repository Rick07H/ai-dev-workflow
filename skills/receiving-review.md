---
name: receiving-review
description: How to react to review findings (from a reviewer agent, a code review or a person). Verify each one against the real code before changing anything.
---
# Receiving review
Adapted from obra/superpowers (receiving-code-review).

A finding is a hypothesis about the code, not an order. Technical correctness beats social agreement.

1. Read it fully. Restate it in my own words; if I do not understand one item, ask before touching any.
2. Verify against the code: does the cited file and line exist and say that? Does the cited consumer exist (grep, never memory)?
3. Judge it for this project: does it break something that works? Is there a reason the code is this way?
4. Answer with a technical acknowledgement ("confirmed at x:42, fixing") or a disagreement with proof ("x:42 has no callers: grep is empty").
5. Log the outcome (fixed / dismissed with proof / sent to the human / later).
6. Implement one finding at a time, verifying each. Blockers first, then simple adjustments, then design changes.

Forbidden: performative agreement ("You are absolutely right!"), "already applying" before verifying, applying the whole list and verifying once at the end.
A finding without file and line is not a blocker: ask for the evidence or dismiss it.
A finding that survives the second round goes to the human, not to a third attempt.
