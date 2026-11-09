## What it does

`brainstorming` turns a vague idea into a design you have approved in conversation, before a spec or any code exists. It is the front door of the Matt flow. The first phase is open exploration: one question at a time, a playback of what the agent heard, and two or three concrete approaches with tradeoffs. The second phase hands the remaining decisions to [grilling](https://aihero.dev/skills-grilling), which maps the decision tree and asks the frontier questions in rounds. [domain-modeling](https://aihero.dev/skills-domain-modeling) records terms and hard-to-reverse decisions when they qualify.

Its defining constraint is that it writes no design document and no plan. The design lives in the conversation, and the handoff is [to-spec](https://aihero.dev/skills-to-spec), then [to-tickets](https://aihero.dev/skills-to-tickets). It is user-invoked.

## When to reach for it

You invoke this by typing `/brainstorming`, and the agent won't reach for it on its own. Reach for it at the start of a change when the idea is still vague and the design is not written down. It is the front door for a new feature, a new project, or any request whose intent, constraints, or success criteria are still thin.

| What you have | Reach for |
| --- | --- |
| A design or plan that already exists and needs pressure-testing | [grill-with-docs](https://aihero.dev/skills-grill-with-docs) in a repo, or [grill-me](https://aihero.dev/skills-grill-me) outside one |
| A conversation that is ready to become a spec | [to-spec](https://aihero.dev/skills-to-spec) |
| A design question that needs a runnable answer | [prototype](https://aihero.dev/skills-prototype) |
| An effort too large for one session | [wayfinder](https://aihero.dev/skills-wayfinder) |

## Prerequisites

The skill itself writes no files, but its handoff does: `to-spec` and `to-tickets` need [setup-matt-pocock-skills](https://aihero.dev/skills-setup-matt-pocock-skills) to have configured an issue tracker. Run that once before the handoff. `domain-modeling` may write `GLOSSARY.md` or an ADR when a term or decision qualifies. A runnable visual question goes through [prototype](https://aihero.dev/skills-prototype), which needs the project's normal tooling.

## Two phases

The skill deliberately splits the conversation in two:

| Phase | Who runs it | What it settles |
| --- | --- | --- |
| Open exploration | `brainstorming` | intent, constraints, success criteria, two or three approaches |
| Decision tree | [grilling](https://aihero.dev/skills-grilling) | the remaining decisions, by frontier and round |

Do not run a second decision tree beside `grilling`. Phase 1 is about what and why; phase 2 is about the decisions that hang off it. When a term or a hard-to-reverse decision qualifies, `domain-modeling` records it. That is the only file output in the flow, and it is a glossary or an ADR, not a design brief.

## Common questions

**Is this just `grill-with-docs`?**
No. `grill-with-docs` starts from a design that already exists and pressure-tests it. `brainstorming` starts from a vague idea, does the open exploration, then hands the decision tree to `grilling`. It is the front door, not the pressure test.

**Does it write a design document?**
No. The design is approved in the conversation, and `to-spec` writes the spec. If you want a written design, run `/to-spec` after the approval.

**Can it invoke `to-spec` or `to-tickets`?**
No. Both are user-invoked, and a user-invoked skill cannot call another user-invoked skill. It tells you to run them.

**What happened to the visual companion?**
It is gone. For a mockup, layout, diagram, or side-by-side comparison, the skill uses a text sketch or calls [prototype](https://aihero.dev/skills-prototype) for a runnable artifact. It never starts a browser companion.

## It's working if

- The design is approved in the conversation before any implementation starts.
- The first questions are open, and the options appear only after the agent knows why.
- `grilling` owns the decision tree; the agent is not running a second interview beside it.
- No design document and no plan file appear in the repo.
- The handoff is a clear instruction to run `/to-spec`, then `/to-tickets`.
- A visual question ends in a text sketch or a `prototype`, never a browser companion.

## Where it fits

`brainstorming` is the user-invoked front door of the Matt flow:

```txt
brainstorming → to-spec → to-tickets → implement
```

It comes before anything is written as a spec. Its closest neighbours are [grill-with-docs](https://aihero.dev/skills-grill-with-docs), which pressure-tests a design that already exists, [grilling](https://aihero.dev/skills-grilling), the decision-tree primitive it calls, [domain-modeling](https://aihero.dev/skills-domain-modeling), which records terms and ADRs, and [prototype](https://aihero.dev/skills-prototype), which answers a runnable design question. When you are unsure which skill or flow fits, [ask-matt](https://aihero.dev/skills-ask-matt) routes you.
