---
name: spiral
description: The review cycle. One builder, independent read-only reviewers triggered by what changed, severity labels and a two-round limit. Use when building, changing or publishing anything.
---
# The spiral
**One builds, several criticize.** Parallelize the criticism, serialize the building. Validation must not depend on the builder's own judgment, which is exactly where the blind spot is.

## Which reviewer fires (by the nature of the change, not its size)
| What happened | Reviewer |
|---|---|
| Changed project code | request-critic + a general code review |
| Touched something shared (root config, a route another service calls, a resource name, a CI trigger, an API contract) | + regression-critic |
| Produced something to look at (PDF, page, screenshot) | + a critic that opens the rendered result |
| Published to production | + a critic that checks what is actually running |
| Touched auth, sensitive data or public input | + a security review |
| Conversation, research, decisions | none |

The human can say "no spiral" to skip, or ask for one reviewer on demand.

## Do not use a reviewer where a command answers
`build`, `tsc`, `eslint`, tests, a `curl` for status. Reviewers are for what has no automatic oracle: scope, architecture, finish, clarity.
A hook that syntax-checks every edit (about 100 ms) is worth more than any reviewer for syntax.

## Dispatch contract
A subagent does not see the conversation. Every dispatch carries: the literal request (or its path), what changed (files or the diff command),
the project path, and what was deliberately left out. Without a reference the reviewer must refuse ("no reference") instead of guessing.
At closing, dispatch reviewers in parallel in one message (they only read). Never parallelize building.

## Severity and the two-round limit
`BLOCKS` wrong result, data loss, scope unmet: fix and re-run only the reviewers that blocked. `ADJUST` works but a better path costs the same: fix if cheap.
`NOTE` does not block now: write it down. **After two rounds, if a blocker survives, stop and call the human.** A spiral without a limit never ends.
A finding I believe is wrong goes to the human with both sides; I do not obey in silence or dismiss in silence.

## Report
Never paste raw reviewer output. One line when clean; otherwise: automatic checks, reviewers (with counts), fixed this round, noted for later, open decisions.
