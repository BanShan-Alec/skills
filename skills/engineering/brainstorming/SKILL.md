---
name: brainstorming
description: "[matt] 在写 spec 前，把模糊想法梳理成经过确认的设计。"
disable-model-invocation: true
---

# Brainstorming

You are good at building. This skill finds out what your human partner actually wants, and why, before a spec or code exists. It is the front door of the Matt flow: explore the idea, use `grilling` to settle the decisions, and use `domain-modeling` when a term or a hard-to-reverse decision needs a record.

It does not write a design document or an implementation plan. The design lives in the conversation. When it is approved, the human runs `/to-spec`, then `/to-tickets`.

## What this skill may call

This skill is user-invoked. It may call the Skill tool for model-invoked skills:

- `grilling` for the decision tree and the frontier questions.
- `domain-modeling` when a term or a decision qualifies for a glossary entry or an ADR.
- `prototype` when a design question needs a runnable answer.

It must not call `to-spec`, `to-tickets`, `grill-with-docs`, or `grill-me`. Those are user-invoked. Tell the human to run them instead.

`domain-modeling` may write `GLOSSARY.md` and ADRs. That is its output, not a design brief. This skill itself writes no design or plan file.

## First: What Do You Actually Know?

Before you reply, ask yourself: what do I know about what they want, and why?

- **Everything that matters is in the request** ("make the icon cornflower blue"). This is a quick, clear task. Do it, and say what you did. This skill is not needed.
- **Something non-trivial is missing.** Start the conversation.

When the conversation is needed, work in this order:

1. Explore the project and the context.
2. Ask open questions, one at a time, and play the answers back.
3. Lay out two or three concrete approaches with their tradeoffs, and recommend one.
4. Call the Skill tool with `grilling` once the idea and the approaches are clear. Give it the settled context and let it work the remaining decisions.
5. Call the Skill tool with `domain-modeling` when a term or a decision qualifies.
6. Present the design in the conversation, section by section, and get approval.
7. Tell the human to run `/to-spec`, then `/to-tickets`.

Do not run your own decision-tree interview in parallel with `grilling`. Phase 1 is open exploration, phase 2 is the decision tree. If a decision is already settled, say so and do not reopen it.

If the human asked for brainstorming, end the first message with the conversation. If they did not, offer them a one-line way to skip it, like "Or if you'd rather I just dive in, say so."

## Look Before You Ask

In an existing project, or when they've given you context (a spec, a plan, a handoff, files they pointed at, earlier conversation), dig in before your first message. Read what they referred to and the code or material it connects to. Keep reading until you can explain how the relevant parts work today and what this change would touch. Never ask what the project or their context already answers, or reopen what they've already decided.

## Your First Message

Move the work forward. If they've already said what they want (a spec, a plan, a detailed request), aim for about 200 words for the whole message. Echo their request back in your own words, so they can see whether you've got its shape: what they want, who it's for, and why, as far as they've said. Add what you found that bears on it. If you found a constraint, a conflict, or a cheaper path they may not have considered, say so plainly. End with one line inviting corrections.

Then ask about the biggest thing their request leaves unsettled. If they haven't told you why they want it, ask about that, in their own terms, with no example answers attached. If they have told you, ask about the one open question whose answer would change what gets built most. When its choices can be named, sketch each concretely, with what it trades off and which you'd pick. If nothing like that is open, and there is one sensible way, end with the short design itself and ask them to approve it.

If they haven't said what they want, ask one open question about the biggest thing their request leaves unsettled. Say why you're asking: what the answer would change about what you build.

## The Conversation

Ask a question only when the answer would change what gets built and neither the request nor the project answers it. Otherwise, state your call and your reason as a proposal they can correct, and move the work forward. Process steps are your calls: writing notes, where to look, how to show something. Do them and say so. Ask one at a time. Use plain language, pitched just a little above where your human partner is. Match their vocabulary; never use process jargon. You never need to quote this skill to your human partner.

Be clear and concise. Lead with what matters. Avoid jargon. When you report what you found, give them the most important findings and offer the rest.

**Get them describing.** Until you know why they want it, ask open questions, with no example answers attached. Their own words carry intent that your options can't. Once you know why, when a decision has choices you can name, sketch each concretely, with what it trades off and which you'd pick. When they say "just guess" or "what do you think?", propose something concrete.

**How it gets made.** Every project rests on choices about medium, tools, materials, and resources: the platform, programming language, and libraries for an app; the medium for a piece of art. Read from how they talk which of those choices they want to make. Someone who raises the how or asks about trade-offs wants the options with your pick. Someone who talks about outcomes is handing you the how: make those calls and state each in a line. When there's existing work, build on what it already uses. Any choice you make goes in the design as your call, never as something they agreed to.

**Ground to cover.** This is territory, not a script. Never read these out as questions:

- what kind of thing this is, and what makes it special
- why now, and what success looks like to them
- goals, non-goals, and anti-goals (what would make this a failure even if it technically works)
- prior art: what they've seen elsewhere, loved or hated
- current state: what exists now, what they've tried
- the details they care about

**Make every question specific** to their project and what they've told you. Ask Socratically, the way a sharp colleague would: build each question on their last answer or on something you found, so it helps them think through a consequence or a case they may have missed. When the reason isn't already plain, say what you're hoping to learn or what the answer would change. A proposal they can correct, plus your reason for it, often beats a question.

**Do recon.** Once you have a bit of grounding and looking further would help, go look: deeper into their codebase or project, their own files and data, or the web. Say what you looked for and what you found.

**Lay out the approaches.** Once you understand what they want, and before you call `grilling`, put the ways of building it in a message of its own. Come up with several real alternatives and drop the weak ones, including any that work against why they want it and any the existing work rules out. Sketch the two or three that remain concretely enough to picture, grounded in what the project actually does, with what each trades off. Recommend one and say why, then ask which way they want to go. When there's genuinely one sensible way, say so in that message and explain why the others don't fit.

**Show, don't tell.** Whenever seeing would help more than reading, sketch it in text: a few lines of what they'd see. For a mockup, layout, diagram, or side-by-side comparison, call the Skill tool with `prototype` and let it build the throwaway artifact. `prototype` is the only visual tool this skill uses.

**Spike to feel things out.** Agentic work is waterfall, but very, very fast. A quick throwaway build is often the cheapest way to learn what they want or whether something works. Offer one when it would help. When they just want to spike, get out of the way. Spikes get no tests or minimal ones, aren't bulletproof, and skip the plan, implementation, and review process. Bring what the spike taught you back into the conversation.

## Play It Back

Play back as you go. As soon as you understand one part well enough to describe it (what it's for and who it serves, say, or how one piece behaves), describe that part back in about 200 to 300 words, then return to questions about the next part. Playback and questions alternate through the whole conversation; the last chunk covers whatever is left.

Only what they said goes in as theirs. Anything you filled in goes in as your proposal, with your reason. End each chunk by asking what's wrong or missing.

Before you send a chunk, check it: does it describe something they'll look at, like a page, a screen, a schedule, or a printout? If so, put a text sketch next to the description. If the look itself is theirs to decide, call the Skill tool with `prototype` when a runnable variant would answer it; otherwise keep the sketch in text.

## Hand Off the Decisions to Grilling

Once the idea is clear and the approaches are on the table, call the Skill tool with `grilling`. Give it the settled context and the open decisions. It will map the design tree, ask the frontier questions in rounds, and attach a recommended answer to each. Let it run its process; do not run a second interview beside it.

`grilling` may ask questions that phase 1 did not need. Answer from the conversation where you can, and put the real decisions to the human. Do not guess at a decision the human has not made.

When a term resolves, or a decision is hard to reverse, surprising without context, and a real trade-off, call the Skill tool with `domain-modeling` so it can update `GLOSSARY.md` or write an ADR. Skip it when none of those gates is met.

## The Design

When `grilling` settles the decisions, present the design in the conversation. Scale each section to its complexity: a few sentences if straightforward, up to 200 to 300 words if nuanced. Ask after each section whether it looks right so far. Cover:

- architecture
- components
- data flow
- error handling
- testing

Be ready to go back and clarify if something doesn't make sense.

**Design for isolation and clarity.** Break the system into smaller units that each have one clear purpose, communicate through well-defined interfaces, and can be understood and tested independently. For each unit, you should be able to answer: what does it do, how do you use it, and what does it depend on? Can someone understand what a unit does without reading its internals? Can you change the internals without breaking consumers? If not, the boundaries need work.

**Working in existing codebases.** Explore the current structure before proposing changes. Follow existing patterns. Where existing code has problems that affect the work, include targeted improvements as part of the design, the way a good developer improves code they're working in. Don't propose unrelated refactoring. Stay focused on what serves the current goal.

<HARD-GATE>
Nothing gets built until your human partner approves the design in the conversation. Building includes writing product code, scaffolding, installing dependencies, creating projects, and invoking an implementation skill. Reading and exploring are fine.

Two exceptions. If they opted out of the questions, the skill is done and the gate goes with it. A spike they said yes to may be built; it stays labeled throwaway, and keeping what it produced is a new request that comes back through this gate.
</HARD-GATE>

## Hand Off to the Spec and Tickets

After the design is approved, tell the human to run `/to-spec`, then `/to-tickets`. Do not write a design document or a plan. The spec is `to-spec`'s job; the tickets are `to-tickets`'s job. Keep the conversation intact for that handoff.

If the human asks for a written design before the spec, say that the spec is the written artifact and route them to `/to-spec`. If they want a plan without a spec, say that `/to-tickets` is the plan.

## Red Flags

| Thought | Reality |
|---------|---------|
| "I'll write the design doc" | No design doc. The design lives in the conversation; `to-spec` publishes the spec. |
| "I'll call to-spec myself" | It is user-invoked. Tell the human to run it. |
| "I'll skip grilling, the idea is clear enough" | If decisions remain, call `grilling`. Do not run a second decision tree beside it. |
| "I'll offer a menu of what they might want" | Options steer. Ask them to describe it first. |
| "I'll fill in sensible defaults" | Good. Say them out loud. A default they never heard is one they could not reject. |
| "They said 'sounds good' to the idea" | Approval covers what you showed them. The design is not approved until you present it. |
| "The spike works, I'll keep building on it" | Keeping it is a new request. Back through the gate. |
| "I'll write a plan after the design" | No plan. `/to-tickets` turns the spec into tickets. |

## Key Principles

- **One question at a time** in the open exploration.
- **Open questions first**, options only after you know why.
- **Play it back** in 200 to 300 words, then ask what's wrong or missing.
- **Two or three approaches**, not one.
- **Grilling owns the decision tree**, not this skill.
- **Approval before implementation**, in the conversation.
- **No design doc and no plan.**
