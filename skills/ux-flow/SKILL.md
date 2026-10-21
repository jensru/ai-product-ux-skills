---
name: ux-flow
description: Design a flow as a guided path to the user's goal - every step actionable, with visible impact, clear about why it matters now and what it teaches - written per step as before, during and after, acknowledged as lightly as the change allows. Use when a task, form or feature needs its steps designed before screens are built, when users drop out and nobody can say where, when a flow is a stack of form windows, or when every action answers with a toast.
---

# UX Flow

Category: **Concept**

|  |  |
|---|---|
| **Use when** | A task, form or feature needs its steps designed · users drop out and nobody can say where · the flow is a stack of form windows · every action answers with a toast or a dialog |
| **Skip when** | The steps are right and only the wording is weak: `ux-text`. The flow exists and needs judging, not designing: a review (separate, not in this collection) |
| **Needs** | The user's goal and what brings them here: a ticket, a brief, interview notes (no skill in this collection produces them) |
| **Produces** | The goal and its aha, a step table with why, before, during, after and acknowledgement per step, and the ways out |
| **Then** | `ux-text`, then `ux-build-plan` when someone else builds it |

## Before you start

Look for the user's goal: what they want to have at the end, in their words, and what happened just before they came.

Found it: build on it and say in one line what you are building on.
Not found, or only a feature request ("add a filter"): write the goal and the trigger yourself at the top, marked **(assumed)**. A flow without a goal leads nowhere in particular, and every step after that inherits it.

## Every flow is an onboarding

Onboarding has one rule that holds for every flow: lead the user to their goal as fast as possible, and let them reach the moment where it pays off (the aha) inside the flow, not after it.

So every step has to:

- **be actionable**: the user does something, not reads something
- **have impact**: something visibly changes because of it
- **say why it matters now**, on the way to the goal
- **teach how the product works**, by doing it, not by explaining it
- **make the user want to do it**: they understand what this step gets them

A step that cannot say what it gets the user is a step to cut or merge.

## Before, during, after

Every step, down to each micro-interaction, has three moments. The structure follows Krystal Higgins, [Better Onboarding](https://abookapart.com/products/better-onboarding).

| Moment | What the user gets |
|---|---|
| **Before** | What this step will bring them. What they need ready for it (documents, numbers, a photo, a decision) and how to prepare |
| **During** | Help to finish it correctly. A way to fix errors without losing work. More information for those who want it, out of the way for those who do not |
| **After** | That it worked. What changed. What they can do next, because of this step |

The after-moment is where flows usually go quiet. "Saved" answers whether the system wrote, not whether the user is further.

## Acknowledge, don't announce

Not every step needs a message. Material distinguishes [confirmation and acknowledgement](https://m2.material.io/design/communication/confirmation-acknowledgement.html): confirm before an action only when it cannot be undone, and acknowledge after an action in the lightest form that makes the change clear.

- The change itself is often the acknowledgement: the item moves, the counter goes up, the next step opens.
- A toast or message only where the change happens somewhere the user cannot see.
- Undo afterwards instead of "are you sure" beforehand.
- A micro-animation can show what was just done and where the next step is. One movement that carries meaning, not decoration.

Every extra toast and message makes the interface heavier.

## Never a menu

Do not answer the three moments by picking from a list (an undo chip here, a tooltip there, a success animation). Anything picked from a menu is the average interaction, and generated flows across unrelated products end up looking the same. The answer comes out of this product's situation:

> *From the menu:* undo chip for five seconds, success animation, next step as a primary button.
> *From the product:* the case now sits where cases will always sit, and assigning an assessor waits beside it as the next target.

Build modern interactions where they shorten the step (the system fills in what it already knows, inline editing, autosave with undo, a photo instead of typing), not a sequence of form windows. The concept knows what technology makes possible and proposes it as variants where it helps (AI suggestions, image upload, a chat), but describes only what the user experiences. Data, services and the build itself are translated afterwards (`ux-build-plan`).

## Each step makes sense

From the GOV.UK [form structure](https://www.gov.uk/service-manual/design/form-structure) guidance and its [question pages](https://design-system.service.gov.uk/patterns/question-pages/):

- Every step makes sense on its own and does not overwhelm.
- Ask only what is needed, and nothing the system already knows.
- What is mandatory is clear; what is optional is marked.
- Before the flow starts, say what documents or information the user will need.

## Check as you go

Walk the flow against a usability standard while designing it, not afterwards: [Nielsen's ten heuristics](https://www.nngroup.com/articles/ten-usability-heuristics/) or ISO 9241-110. Visibility of system status, user control, error prevention and recovery, recognition over recall: if the three moments are done well, these are already met. Where one is not, the step is not finished.

## What to write down

1. **Goal and aha.** What the user has at the end, and the one moment where it pays off.
2. **The steps.** One row per step:

| Step | Why now (on the way to the goal) | Before | During | After | Acknowledgement |
|---|---|---|---|---|---|

   Describe actions on components ("takes a photo of the receipt"), never layouts. One line per cell.
3. **Ways out.** No step ends without a way forward. One line per dead end with its way out (data missing, step skipped, the user leaves and comes back).

Leave out final wording (`ux-text`), technical detail and layout (`ux-build-plan` and the build), and how the flow was produced.

## Where it sits

**`ux-flow`** → `ux-text` → `ux-build-plan` → build → `ux-validate`
