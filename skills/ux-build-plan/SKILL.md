---
name: ux-build-plan
description: Translate a UX concept (flow and text) into a build plan - the technical steps, data, components and services each concept step needs - without changing the experience, and send back what the concept asks that cannot be built as described. Use when a concept from `ux-flow` and `ux-text` is ready and someone has to build it, when developers receive a concept instead of a build briefing, or when a coding agent is about to implement a flow.
---

# UX Build Plan

Category: **Build**

|  |  |
|---|---|
| **Use when** | A concept from `ux-flow` (and usually `ux-text`) is ready to build · developers or a coding agent get a concept, not a briefing · the concept proposes an interaction nobody has built here before (image upload, AI suggestions, chat) |
| **Skip when** | The change is small enough that whoever builds it can go straight from the concept · the concept is not settled yet: finish it in `ux-flow` first · the build exists and needs checking against the concept: `ux-validate` |
| **Needs** | The concept: goal, steps with before, during, after and acknowledgement (`ux-flow`), and the text handover (`ux-text`) if there is one |
| **Produces** | A build plan that traces every item to a concept step, the technical decisions with one recommendation each, and a list of what goes back to the concept |
| **Then** | Build. `ux-validate` if the build has to be checked against the concept |

## Before you start

Look for the concept: the goal, the steps, and for each step what the user gets before, during and after. It usually comes from `ux-flow`, with text from `ux-text`.

Found it: build on it and say in one line what you are building on.
Not found, or only a feature list: say so and offer to run `ux-flow` first. A build plan without a concept invents the experience, which is the concept's job.
Told to go ahead anyway: do, but write the assumed experience at the top of the plan, marked **(assumed)**.

## The concept owns the experience

The concept describes what the user lives through. It carries no technology on purpose. This skill adds the technology and leaves the experience as it is.

- **Translate, don't redesign.** Every concept step becomes the technical steps that make it happen: data it reads and writes, components, services, states the code has to model.
- **Nothing extra.** No feature, state or screen the concept does not ask for. If the plan needs something the concept left out (an error case, a loading state), add it and mark it as added.
- **Push back, don't bend.** When a concept step cannot be built as described, or only at a cost out of proportion, do not quietly build something else. Write it on the list back to the concept, with what would work instead.

## What to write down

1. **Building on**: the concept, in one line.
2. **The plan.** One block per concept step, using the concept's step names:
   - what the user gets in this step (one line from the concept)
   - the technical steps that deliver it
   - data and services it depends on
   - states the code models for it
3. **Technical decisions.** Each open choice (where data comes from, how a conflict is prevented, which service reads a receipt) with one recommendation and the reason.
4. **Added by the plan.** Everything that is not in the concept, marked.
5. **Back to the concept.** What cannot be built as described, why, and the alternative.

Leave out how the plan was produced: no skill names, no process notes.

## What this skill does not do

It does not change goal, steps or text of the concept; that goes back to `ux-flow` or `ux-text`. It does not check the finished build; that is `ux-validate`.

## Where it sits

`ux-flow` → `ux-text` → **`ux-build-plan`** → build → `ux-validate`
