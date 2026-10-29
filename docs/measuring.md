# Measuring whether the reviewers are worth it

Without measurement I cannot tell which reviewer earns its cost. After each review round, once I have decided what happens to each finding,
I append one line per finding to a CSV (only the builder writes it, because the outcome is a decision):

```
date,project,source,label,title,outcome
2026-10-28,example-project,regression-critic,BLOCKS,Renamed volume would orphan the database,fixed
```

- **source:** reviewer name, `code-review`, `security-review`, `second-model` or `person`
- **label:** `BLOCKS`, `ADJUST`, `NOTE`, or `CLEAN` for a round with no findings (so a reviewer that never finds anything shows up)
- **outcome:** `fixed`, `dismissed` (with proof), `human`, `later`

A monthly read answers three questions: which source has the best hit rate, which reviewer has found nothing real in many rounds
(a candidate to remove), and whether a second model reviewing is worth keeping as a fixed step.

Tokens are not logged, because they cannot be measured per subagent.

**Status:** the log file exists but has no entries yet, so there are no numbers to publish.
