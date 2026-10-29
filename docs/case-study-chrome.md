# Case: the assistant that "had no browser"

A real episode, kept short. It shows the method catching, and then fixing, a failure of the assistant itself.

## What happened
I asked the assistant to log in to freelance sites and update profiles. It answered that it had no browser access.
It said this more than once, and a second chat in the same editor then *did* drive Chrome. I called out the inconsistency.

## Root cause (not the patch)
The assistant had stored the answer in its own memory weeks earlier and did not read it before claiming a limit.
The facts, once checked:
- The browser tools exist only in a session started from a terminal with `claude --chrome`.
- Chat panels inside the editor never receive them, so a second chat that "worked" was simply started the other way.
- My first fix was also wrong: I told the user to open another editor chat. Following that advice, the new chat also refused.

## What changed because of it
1. The rule was written where every future session reads it first: the memory index of both workspaces, with the exact startup command.
2. A new line in the working rules: **before claiming a capability limit, read the memory and verify the claim.**
3. The ready-to-paste prompt for the browser session lists its stop conditions (captcha, identity verification, payment) and the actions that need a human yes (submitting a profile, sending a proposal).
4. Result: the profile and four services were created and a job search was run in that session, with no proposal sent without approval.

## Why it is in this repo
It is the method working as intended: the failure was reported with evidence, traced to a cause ("I did not read what I had already written"),
and turned into a rule instead of an apology. Evidence-before-claims applies to the assistant's statements about itself too.
