---
name: evidence-before-claims
description: No claim of done, passing, fixed or deployed without running the proving command in this message and reading the output. Also applies when a subagent reports success.
---
# Evidence before claims
Adapted from obra/superpowers (verification-before-completion).

**Law: no status claim without fresh evidence.**

Gate before any success sentence: (1) which command proves this, (2) run it fully now, (3) read all of the output and the exit code,
(4) does it confirm the claim? If not, state the real status with the output. (5) Only then claim, with the evidence attached.

| Claim | Proof | Not enough |
|---|---|---|
| Tests pass | runner output, 0 failed | an earlier run, "I did not touch that" |
| Build works | the build command, exit 0 | lint passed |
| Bug fixed | the original symptom no longer reproduces | the code changed, "makes sense" |
| It is live | a request from outside returns 200 and the process is up | "the deploy command printed no error" |
| A subagent finished | the diff shows the change | its report says "done" |
| Generated file is right | open it and look | the source of the file looks right |

Red flags: "should", "probably", "seems to"; satisfaction before proof ("Great!", "Done!"); committing without running anything in this message;
trusting a subagent's success without reading the diff; partial verification.
