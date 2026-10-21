---
name: ux-validate
description: Check a build plan or a finished build against the UX concept it came from - step by step, before, during, after and acknowledgement, and the text handover - and list what matches, what is missing, what was added and what was changed. Use when a concept was handed to developers or a coding agent, before a release, or when nobody can say whether what was built is what was designed.
---

# UX Validate

Category: **Check**

|  |  |
|---|---|
| **Use when** | A concept was translated by someone else (a developer, a coding agent) · a build is about to be released · the build and the concept seem to have drifted apart |
| **Skip when** | The person who wrote the concept built it and the change is small · the concept itself needs judging, not its translation: a review (separate, not in this collection) |
| **Needs** | The concept (`ux-flow`, `ux-text`) and what was made from it: a build plan (`ux-build-plan`) or a running build |
| **Produces** | A comparison per concept step, a list of deviations each with who fixes it, and a verdict |
| **Then** | Deviations go back to the build, or to the concept if the build found something the concept missed |

## Before you start

Look for both sides: the concept, and the plan or build made from it.

Found both: say in one line what you compare with what.
One missing: say which. Without the concept there is nothing to validate against; without the build there is nothing to validate.

## Validate against the concept, not against taste

The question is not "is this good" but "is this what the concept describes". Walk the concept step by step and check the build there:

| In the concept | Check in the build |
|---|---|
| Goal and aha | Does the user reach the goal on the path the concept describes, and does the payoff moment happen where the concept puts it? |
| Before | Does the user see what the step brings and what to have ready? |
| During | Is the help there, can errors be fixed without losing work? |
| After | Does the user see that it worked, what changed, what comes next? |
| Acknowledgement | Is it as light as the concept says, or did toasts and dialogs creep in? |
| Text | Are the strings the ones from the handover, with the same terms? |

Then the other direction: what is in the build that the concept does not ask for? Extra steps, states and features are deviations too.

## What to write down

1. **Compared**: concept and build, in one line.
2. **Per concept step**: matches, missing, changed, each in one line with where to see it.
3. **Added by the build**: everything not in the concept.
4. **Deviations**, ranked by how much they change the experience, each with who fixes it: the build (it drifted) or the concept (the build found a real gap).
5. **Verdict** in two sentences: does the build deliver the concept, and what is the one thing to fix first.

## What this skill does not do

It does not redesign and does not review usability or accessibility in general; it checks one thing against another. It does not fix the deviations.

## Where it sits

`ux-flow` → `ux-text` → `ux-build-plan` → build → **`ux-validate`**
