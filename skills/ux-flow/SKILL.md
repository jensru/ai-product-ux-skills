---
name: ux-flow
description: Turn a task into a click path written as a sequence of states, one thing per step, with every state a screen can be in (empty, loading, error, success, partial) and a way out of each. Use when a task in working software needs its steps designed before screens are built, when a form or process has to be split into steps, when users get stuck and nobody can say in which state, or when a build only knows "loading, data, error".
---

# UX Flow

Category: **Flow**

|  |  |
|---|---|
| **Use when** | A task in existing or business software needs its steps designed · a long form or process has to be cut into steps · users get stuck and nobody can say where · the implementation only models `loading`, `data` and `error` |
| **Skip when** | An onboarding or activation flow for a new product, built around one peak moment: a different job (`user-flow`, separate, not in this collection). The flow exists and needs judging, not designing: `ux-check` |
| **Needs** | A context brief with task, trigger, routine and success criterion (`ux-context`) |
| **Produces** | A step table with entry state, action, system reaction and exit per step, a state catalogue per view, and a dead-end list |
| **Then** | Build the screens (your own screen step), then `ux-text` |

## Before you start

Look for the context brief: task, trigger, routine and success criterion. It usually comes from `ux-context`.

Found it: build on it and say in one line what you are building on.
Not found: say what is missing and offer to run `ux-context` first.
Told to go ahead anyway: do, but write the assumed task, routine and success criterion visibly at the top of the flow.

The routine matters most. A flow for someone who does this once a year and a flow for someone who does it forty times a day are different flows, even when the data is the same.

## The logic this skill follows

Two bodies of published, tested guidance, used for what each does best.

**GOV.UK** for the structure of a task. [Do the hard work to make it simple](https://www.gov.uk/guidance/government-design-principles) is the fourth UK government design principle, and the Service Standard asks teams to [solve a whole problem for users](https://www.gov.uk/service-manual/service-standard), not the part that happens to sit in one system. For forms the service manual recommends [starting with one thing per page](https://www.gov.uk/service-manual/design/form-structure) and asking only what the service really needs. The Design System turns that into patterns: [question pages](https://design-system.service.gov.uk/patterns/question-pages/), [check answers](https://design-system.service.gov.uk/patterns/check-answers/), [confirmation pages](https://design-system.service.gov.uk/patterns/confirmation-pages/), [complete multiple tasks](https://design-system.service.gov.uk/patterns/complete-multiple-tasks/).

**Android and Material** for movement and state. Android's [principles of navigation](https://developer.android.com/guide/navigation/principles) say that Back returns to the previous state and a deep link lands with a sensible back stack. Material documents [interaction states](https://m3.material.io/foundations/interaction/states/overview) and offers undo after the fact through a [snackbar](https://m3.material.io/components/snackbar/overview) rather than a confirmation before it.

Neither is a style to copy. Both are evidence about what works, and a flow that departs from them should be able to say why.

## One thing per step, read correctly

"One thing per page" means one decision, one question or one piece of work per step, so the user never has to hold two in their head. It does not mean one field per page in a tool used all day.

| Routine | What one thing per step becomes |
|---|---|
| Rare | Literally one question per page, check answers before commit, a confirmation page after |
| Occasional | One decision per screen or section, with the rest collapsed until it is needed |
| Daily | One decision per interaction on a dense screen: selecting, acting and seeing the result without leaving the list. The step is the action, not the page |

The test is the same for all three: can you name the one thing this step asks of the user? If the answer has an "and" in it, the step is two steps.

## Procedure

**1. Fix the ends.** Start state from the trigger in the brief, end state from the success criterion. "Forty new applications, none reviewed" to "five marked for a call, the rest sorted". If the end state is "the user has seen the page", the flow has no end.

**2. List what the system needs.** Every piece of information and every decision the task requires. For each one ask why it is needed, and whether the system could know it already. GOV.UK calls this a question protocol. Whatever the system can infer, it infers and shows for confirmation. That is the hard work that makes it simple.

**3. Cut into steps**, one thing each, in the order the user thinks about the task, not the order the database stores it. Put the question that can end the task early (not eligible, not allowed, nothing to do) first.

**4. Write each step as a state change:**

| Field | Rule |
|---|---|
| Entry state | What is true when the user arrives, including how they got here |
| The one thing | The decision, question or action this step asks for |
| System reaction | What the system does, concretely. "Saves the draft and moves the applicant to Shortlist" |
| Exit | Where the user goes next, and where Back goes. Back never loses entered data |
| Failure | What happens when it goes wrong, and what the user does then |

Describe actions on components ("selects three rows, chooses Move to shortlist"), never layouts. Layout is the screen step's job.

**5. Put the commit where it can be checked.** Anything irreversible or costly gets either a check step before it (GOV.UK check answers) or undo after it (Material snackbar). Prefer undo for anything that can be undone. A confirmation dialog before a reversible action trains people to click through dialogs.

**6. Write the state catalogue** for every view in the flow. See below.

**7. Sweep for dead ends.** Walk every state and ask: can the user go forward, can they go back, and do they know which of the two they should do? A state with no answer to one of these is a dead end.

## The state catalogue

Every view a flow touches can be in more states than the one that was designed. Each state here is one the implementation has to model, or it does not exist in the build.

| State | What the user needs to see |
|---|---|
| **Empty, first use** | What will appear here, and the one action that makes it appear |
| **Empty, no results** | That the search or filter caused it, which filters are active, and how to loosen them |
| **Loading** | That something is happening. For more than about a second, what is happening. Keep the layout stable so nothing jumps when data arrives |
| **Partial** | Which part arrived and which did not, and that the rest is still usable. A list where three of forty rows failed to load is not an error page |
| **Error, recoverable** | What went wrong in the user's terms, what to do, and that their input is still there |
| **Error, system** | That it is not their fault, whether to retry or come back later, and where to get help. GOV.UK has patterns for [there is a problem with the service](https://design-system.service.gov.uk/patterns/problem-with-the-service-pages/) and [page not found](https://design-system.service.gov.uk/patterns/page-not-found-pages/) |
| **No permission** | That the thing exists, that they cannot act on it, and who can |
| **Success** | That it worked, what changed, and what comes next. "Saved" answers whether the system wrote, not whether the user is done |

Not every view has every state. Write down which ones apply and why the others cannot happen. "Cannot happen" is a claim the build will test.

## Session continuity

For flows that take longer than one sitting: what survives when the user leaves mid-flow, where they land on return, and how they see what is still open. GOV.UK's complete multiple tasks pattern is one answer for long applications. In a daily tool, the answer is usually that the list remembers its filter, sort and selection.

## What to write down

The step table, the state catalogue per view, and the dead-end list with one way out each. Next to the feature in the repo, or wherever the screen step will read it.

## What this skill does not do

It does not decide layout, look or final text. Layout belongs to the screen step, words to `ux-text`, recurring solutions to `ux-pattern`. It does not design the emotional arc of an onboarding; that is a separate job (`user-flow`, not in this collection). It does not review a finished flow; that is `ux-check`.

## Where it sits

`ux-context` → **`ux-flow`** → screen → `ux-text` → `ux-pattern` → `ux-check`
