---
name: ux-pattern
description: Turn a gap in a pattern library into a written pattern - the problem it solves, its source in the GOV.UK Design System or Material Design, do and don't, every state, accessibility, a worked example, and a status of "to test" or "decided". Use when a design or review hits a situation the project's library has no answer for, when the same UX question gets answered differently on different screens, when a review finding keeps coming back, or when an agent keeps improvising the same interaction.
---

# UX Pattern

Category: **Build**

|  |  |
|---|---|
| **Use when** | A screen needs an interaction the library does not cover · the same question (how do we filter, how do we confirm) gets a different answer on every screen · a `ux-check` finding recurs across screens · a coding agent improvises the same interaction differently each time |
| **Skip when** | There is no library or style system yet: set one up first (`design-system-bootstrap`, separate, not in this collection). Twelve near-identical components need merging into one: component work, not a pattern (`component-crystallizer`, separate). An agent ignores rules that already exist: an enforcement problem, not a missing pattern (`ground-and-refuse`, separate) |
| **Needs** | The gap, shown in at least one real screen or flow, and the project's existing library |
| **Produces** | One pattern file in the project's library, in a fixed format, marked "to test" or "decided" |
| **Then** | The screen step builds with it, `ux-check` checks against it, and whatever binds your coding agent to the library (`ground-and-refuse`, separate) makes agents follow it |

## Before you start

Look for the project's pattern library: a `patterns/` folder, a design system site, a styleguide, a component catalogue with usage notes.

Found it: search it for the gap first, under every name the gap might have. Say in one line what you searched and what came closest.
Not found: say so and suggest setting up a library first (`design-system-bootstrap`, separate, not in this collection). A pattern with no library around it has nothing to be consistent with.
Told to go ahead anyway: do, but write the pattern as a standalone file and say in its header that no library was checked.

The search is the step that gets skipped. A second pattern for a problem the library already solves is worse than none, because now there are two answers.

## A pattern is a decision, not a component

A component is a thing on the screen: a chip, a table, a dialog. A pattern is the answer to a recurring question: how people filter a long list, how they confirm a destructive action, how they recover from an error. It names components, but it lives one level up, and it can survive a component being rebuilt.

GOV.UK makes the same split, between [components](https://design-system.service.gov.uk/components/) and [patterns](https://design-system.service.gov.uk/patterns/), and its [contribution criteria](https://design-system.service.gov.uk/community/contribution-criteria/) are a good bar for any library: a new pattern has to be **useful** (evidence that several screens or teams need it) and **unique** (it does not repeat something the library has). Before it counts as finished it has to be **usable** (tested with real users, including disabled users), **consistent** (built from existing styles and components) and **versatile** (works in more than the one screen that asked for it).

## Borrow before you invent

Most gaps in a product's library are not new problems. They are problems GOV.UK or Material already researched. Look there first:

| Source | Strong for | Where |
|---|---|---|
| GOV.UK Design System | Forms, questions, errors, check and confirm, long tasks, anything a first-time user must get right | [design-system.service.gov.uk](https://design-system.service.gov.uk/) |
| Material Design 3 | Components and their states, navigation, lists and selection, touch and pointer behaviour, feedback like snackbars | [m3.material.io](https://m3.material.io/) |
| WAI-ARIA Authoring Practices | Keyboard and screen reader behaviour for every widget type | [w3.org/WAI/ARIA/apg](https://www.w3.org/WAI/ARIA/apg/) |

Describe what you take and link it. Do not paste their guidance into the pattern; it goes out of date there and stays current at the source. Where the pattern deviates from the source, say how and why. A deviation without a reason is usually a mistake.

When neither source has an answer, the pattern is an invention. Say so in the Source field. Inventions start as "to test" without exception.

## Procedure

**1. State the problem as a user task.** Take it from the context brief (`ux-context`) or the flow (`ux-flow`) where the gap showed up. "Recruiters need to narrow forty applicants down by several criteria at once and see which criteria are active", not "we need a filter component".

**2. Collect the evidence.** Every screen in the product that meets this problem today, and how each one solves it. Two different solutions are the strongest argument that a pattern is needed.

**3. Find the source** in the table above. Read it fully, including when not to use it.

**4. Write the pattern** in the format below.

**5. Set the status.** "To test" until it has been used in a real screen and checked with users. "Decided" once it has, with the evidence named. This mirrors GOV.UK's [trial and stable](https://design-system.service.gov.uk/community/component-lifecycle-statuses/) statuses, and it keeps an untested idea from spreading through the product with the authority of a rule.

**6. Prove an agent can follow it.** Ask a coding agent to build the situation from step 1 with only the pattern as guidance. If it builds something else, the pattern is ambiguous. Tighten and repeat.

## The pattern format

One file per pattern, named after the task (`filter-a-list.md`, `confirm-destructive-action.md`), in the project's library.

```markdown
# [Pattern name, as a task]

Status: to test | decided (since [date], evidence: [what])

## Problem
The user task and the situation, in two or three sentences. Who meets it how often.

## Source
[GOV.UK / Material / APG link]. What is taken, what deviates and why.
Or: "Invented, no published pattern found. Searched: [where]."

## Use when / Do not use when
Concrete situations for each. The second list prevents the pattern from spreading.

## How it works
The interaction in steps, naming the library's real components and tokens.

## Do / Don't
Pairs. Each Don't is something that has actually happened in this product.

## States
Every state from the catalogue in `ux-flow` that applies: empty, loading, partial,
error, success, no permission, no results. Which ones cannot happen, and why.

## Accessibility
Keyboard path, focus handling, what a screen reader announces, contrast of any
new visual element, target size. Name the WCAG criteria by number and level.

## Text
The fixed wording: labels, buttons, errors, empty states (from `ux-text`).

## Example
One worked example in a real situation of this product, described or sketched.

## Open questions
What is not known yet, and what would settle it.
```

Keep a pattern under two screens of text. A pattern nobody reads before building does not exist.

## Where it goes wrong

**The pattern is written for one screen.** It solves the screen that triggered it and fails the next. Step 2 exists to prevent this: a pattern needs more than one case.

**Everything is "decided" from day one.** Then the first user test that contradicts it becomes a political fight instead of a status change.

**The source is quoted, not linked.** The copy ages, the source moves on, and in a year the pattern contradicts the guidance it claims to follow.

**The pattern contradicts the brand, or the other way round.** A pattern decides behaviour; the look comes from the project's tokens. If a published source prescribes a colour or a shape, take the behaviour and leave the look.

## What this skill does not do

It does not create patterns in advance. A pattern comes from a gap found in real work; a library of patterns written on speculation is a library nobody asked for. It does not build components, merge component variants or bind an agent to the library; those are separate jobs (`component-crystallizer` and `ground-and-refuse`, not in this collection).

## Where it sits

`ux-context` → `ux-flow` → screen → `ux-text` → **`ux-pattern`** → `ux-check`

It is also where `ux-check` sends a finding that recurs: fixing it once on one screen is a ticket, turning it into a pattern fixes every screen that comes after.
