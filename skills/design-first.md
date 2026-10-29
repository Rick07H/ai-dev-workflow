---
name: design-first
description: Gate before any building. Classify the request, present the design, and stop until the human says yes. Use before writing the first line of code, creating files or changing behavior.
---
# Design first

No code, file, scaffold or behavior change before saying what I intend to do and getting an explicit approval.
The ceremony scales with the size of the task; the approval never does.

## 1. Classify out loud
| Path | What it is | Output |
|---|---|---|
| Probe | A feasibility question ("is it possible...") | An answer. Anything built is throwaway and labeled so |
| Bounded | A small change inside a flow that already exists in this repo | A short design in chat, approval, then implement |
| Architectural | New project/subsystem, or a change other code depends on | Questions, 2-3 approaches, design by sections, plan review, approval |

When unsure between two, take the heavier one. The ratchet only goes up: if hidden complexity shows up mid-way,
stop, say so and move up. "I know this kind of app" does not make something bounded; the repo does.

## 2. Rules
- Read before asking. Ask only what the repo cannot answer, one question per message, multiple choice when possible.
- Present approaches with the recommended one first and why. Apply YAGNI.
- Presenting a design and starting to build in the same message skips the gate.
- Each task gets its own classification and its own yes. Approving a probe does not approve the change after it.

## 3. Rationalizations that mean "stop"
"Too simple to need a design" (simple means a two-sentence design, not none) / "it is obvious, I will start while they read" /
"it grew but I am almost done" (say so and move up).

Escape hatch: if the human says "just do it", announce in one line what I am about to do, then do it.
