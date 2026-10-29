---
name: root-cause-debugging
description: Find the root cause before proposing any fix, for bugs, failing tests, broken builds and odd behavior. After three failed fixes, stop and question the design.
---
# Root-cause debugging
Adapted from obra/superpowers (systematic-debugging).

**Law: no fix without a root-cause investigation first.**

1. **Investigate.** Read the whole error. Reproduce reliably. Check what changed (diff, dependencies, config, environment differences).
   In multi-layer systems, instrument each boundary (what goes in, what comes out) and see where it breaks before touching any layer.
   Trace the bad value back to where it is born; fix it there, not where it blew up.
2. **Pattern.** Find a working example in the same codebase, read it fully, list every difference.
3. **Hypothesis.** Write one: "I think X is the cause because Y". Test it with the smallest change, one variable at a time.
   Did not work? New hypothesis, not a fix on top of a fix. Do not know? Say "I do not understand X".
4. **Fix.** Failing test first, one fix at the cause, no refactoring on the side, then verify (see evidence-before-claims).
5. **Three strikes.** Three failed fixes means the design is wrong (misplaced boundary, mixed responsibilities, data with no owner).
   Stop and talk to the human; there is no fix number four without that conversation.

Signs I am guessing: "quick change", "must be cache/network/the OS", "I will fix both at once", "cannot reproduce, but I will patch anyway".
