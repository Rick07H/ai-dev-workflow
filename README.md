# ai-dev-workflow

A working method for building software with an AI coding assistant without trusting it blindly.

**One agent builds. Independent reviewers check before, during and after. Nothing is "done" without evidence.**

I use this daily with Claude Code. The files here are Claude Code skills and subagents, written as plain
Markdown, so the ideas port to any assistant that can load instructions.

## Why it exists

An assistant that builds and also judges its own work has a blind spot: it believes what it just wrote.
This workflow moves the judgment to places the builder cannot reach: a written design that needs an explicit "yes",
a test that must be seen failing, a command that must be run in the same message as the claim, and reviewers
that only read and never edit.

## The cycle

```
BEFORE   design    -> skills/design-first.md        classify the request, present the design, STOP until approved
         plan      -> agents/plan-advocate.md       what did the plan assume without saying?
DURING   logic     -> skills/tdd.md                 a test I saw fail, then the code
         bug       -> skills/root-cause-debugging.md  cause before fix; after 3 failed fixes, question the design
         "done"    -> skills/evidence-before-claims.md  the proving command, run now, output read
AFTER    delivery  -> skills/spiral.md              reviewers triggered by what changed, in parallel
         findings  -> skills/receiving-review.md    verify each finding against the code before acting
CLOSE    branch    -> skills/closing-a-branch.md    green checks, commit, integration choice, record
```

More detail: [docs/workflow.md](docs/workflow.md). A real case: [docs/case-study-chrome.md](docs/case-study-chrome.md).

## The reviewers (`agents/`)

| Agent | One question |
|---|---|
| plan-advocate | Does the plan fix the cause or the symptom, and what did it assume? |
| request-critic | Was what was asked built, nothing less and nothing more? |
| regression-critic | Did this change break something that worked? It reads what is NOT in the diff. |

Each reviewer must attach evidence (file and line, or command output) to every finding, labels it
`BLOCKS`, `ADJUST` or `NOTE`, and may answer "clean" or "no reference" instead of inventing a finding.

## What I decided, and why

- **Two rounds maximum.** Reviewers always find one more thing. After two rounds the open items go to a human.
- **Run a command when a command can answer.** Never ask a model whether the code compiles.
- **Reviewers cannot edit.** They read; the builder decides. A finding I disagree with goes to the human with both sides.
- **Proportional effort.** A one-file change gets at most one reviewer.

## Measuring it

I log every finding from now on (`date, project, source, label, title, outcome`) so I can see which
reviewers earn their cost. See [docs/measuring.md](docs/measuring.md). No numbers yet; I will not invent any.

## Credits and license

Several skills are adapted from [obra/superpowers](https://github.com/obra/superpowers) by Jesse Vincent (MIT):
systematic debugging, brainstorming, test-driven development, verification before completion,
receiving code review and finishing a development branch. I rewrote them for my own constraints,
added the reviewer agents, the trigger rules and the finding log. MIT license, see [LICENSE](LICENSE).

---

## Resumo em português

Método de trabalho com assistente de IA: um agente constrói, revisores independentes conferem antes,
durante e depois, e nada é "pronto" sem prova (comando rodado na hora). Os arquivos são skills e agentes do
Claude Code em Markdown. Parte é adaptada do `obra/superpowers` (MIT), com crédito acima. Autor: Henrique Oliveira.
