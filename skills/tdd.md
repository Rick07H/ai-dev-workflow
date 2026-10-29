---
name: tdd
description: Write the test first and watch it fail, for any feature, bug fix or behavior change in project logic. Also covers the common case of a project with no tests at all.
---
# TDD: the test I saw fail
Adapted from obra/superpowers (test-driven-development).

**Law: no production code without a failing test first.** Wrote code before the test? Delete it and restart from the test.

1. RED: one minimal test, named for the behavior, real code (mock only when unavoidable; assert on results, not on the mock).
2. Watch it fail, for the right reason (the feature is missing, not a typo). Passed on the first run? It tests existing behavior; redo it.
3. GREEN: the simplest code that passes. Nothing "for later".
4. Run the whole suite, not only my file. If something else fails, fix the code, not the test.
5. REFACTOR only while green. Then the next test.

Before writing a test, answer: what change in production code would make this fail? If I cannot say, it tests nothing.

**No tests in the project?** That is the first step, not an excuse. Node: `node --test`. Next/Nest: `vitest`. Python: `pytest`.
Register the new command in the project's checks so later blocks run it automatically.

Exceptions only when the human says so: throwaway probes, generated code, config files.
