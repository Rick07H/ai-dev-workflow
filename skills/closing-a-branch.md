---
name: closing-a-branch
description: Closing ritual for a block of work in a repository. Green checks, commit, an integration choice for the human, and a record for the next session.
---
# Closing a branch
Adapted from obra/superpowers (finishing-a-development-branch).

Work that is not closed is work the next session does not know exists.

1. **Green checks first.** Run the project's lint, types, build and the full test suite. Any failure stops here; no "commit now, fix later".
2. **Repo state.** `git status`, recent log, remotes. Is there a remote? What is the base branch (ask if unsure)? Any changed file that is not mine? List it and ask; never put it in my commit.
3. **Commit.** Match the repo's style: short imperative subject, the *why* in the body. Never skip hooks. Never commit secrets, dumps or generated files.
4. **Integration menu, human decides.** (1) merge locally into base, re-run checks on the result; (2) push and open a pull request; (3) leave the branch. Discard only if asked.
5. **Record.** Move the task to done, turn leftovers into new tasks with what/when/why, and save to memory only what cannot be deduced from the code or git history. State explicitly if a deploy is still pending: a commit is not production.
6. **Clean up.** Remove used worktrees without force; if it refuses because of unsaved files, stop and ask.
