# The workflow in one page

```
                       ┌──────────────────────────────────────────┐
  request ──► classify ─► design (human says YES) ─► plan-advocate ─┐
                       └──────────────────────────────────────────┘ │
                                                                    ▼
   ┌────────────── BUILD, one block at a time (one builder) ───────────────┐
   │  failing test first (tdd) ─► code ─► automatic checks (build/lint/test) │
   │  bug? ─► root-cause-debugging (3 failed fixes = question the design)    │
   │  before saying "done" ─► evidence-before-claims                          │
   └──────────────────────────────────┬────────────────────────────────────┘
                                      ▼
        reviewers by trigger (read-only, in parallel):
        request-critic · regression-critic · rendered-output critic · production-state critic
                                      ▼
        receiving-review: verify each finding against the code, one at a time
                                      ▼
        two rounds max ─► still blocked? the human decides
                                      ▼
        closing-a-branch: green checks ─► commit ─► human picks integration ─► record
```

## Three ideas that carry the rest
1. **Separation of builder and judge.** The builder cannot be the only judge of its own work.
2. **Gates that need a human "yes".** Design approval, integration choice, anything touching production.
3. **Evidence over confidence.** A claim without a fresh command output is not a claim.

## Support pieces (not in this repo yet)
- A hook that syntax-checks each edited file in about 100 ms and blocks on a broken file.
- A per-project file that lists the real check commands (read from `package.json`, not memorized).
- Persistent memory with an expiry date on every "in progress" line, and a monthly review that archives expired ones.
