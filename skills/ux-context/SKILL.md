---
name: ux-context
description: Pin down the one task a screen or flow serves before anything is designed - the task in the user's words, the routine it sits in, the user group, and an observable success criterion. Use when someone asks for a new screen, a redesign or a feature in existing software and nobody has written down who does what how often, when a ticket names a feature instead of a task, or when a review keeps arguing about taste because nobody agreed what the screen is for.
---

# UX Context

Category: **Understand**

|  |  |
|---|---|
| **Use when** | A screen, redesign or feature is requested for software that already exists · the ticket names a feature ("add a filter") instead of a task · the same screen gets redesigned twice because nobody agreed what it is for · a review turns into an argument about taste |
| **Skip when** | A whole product is being defined from nothing, with persona, storyboard and triggers: that is product discovery, not this skill (a skill such as `context-package`, separate, not in this collection). The users themselves are unknown and need researching first: do that research before this skill |
| **Needs** | Evidence about the task: a ticket, interview notes, support requests, a recorded session, analytics, or the person who asked |
| **Produces** | A context brief of half a page: task, trigger, routine, user group, success criterion, constraints, open assumptions |
| **Then** | `ux-flow` |

## Before you start

Look for evidence about the real task: interview notes, support tickets, a session recording, analytics, a written request from the people who do the work.

Found it: build on it and say in one line what you are building on.
Not found: say what is missing and offer to collect it first, by asking the one person who knows or through whatever user research your setup has.
Told to go ahead anyway: do, but mark every line of the brief that is assumed rather than observed with **(assumed)**.

A brief written from the feature request alone describes the feature back to its author. That is the one failure this skill exists to prevent.

## Start with user needs, not with the screen

The first of the UK government design principles is [Start with user needs](https://www.gov.uk/guidance/government-design-principles), and the first point of the [Service Standard](https://www.gov.uk/service-manual/service-standard) is *Understand users and their needs*. Both say the same thing: a need is what someone is trying to get done, in their words, and a feature is one guess at how to serve it. A ticket that says "add a filter to the applicant list" is a guess. The need behind it might be "I have to get forty applications down to five I will call this week", which a filter serves badly and a sort, a shortlist or a bulk action may serve well.

So the brief is about the task, and the screen is not mentioned in it.

## The routine decides the logic

Before anything else, settle how often this person does this task. It decides which design logic applies, and getting it wrong produces a screen that is correct and still wrong.

| Use | Typical case | What the design owes the user |
|---|---|---|
| **Rare** (yearly, once) | Applying, registering, a one-off request | Guidance. One thing per step, plain language, nothing to learn, a check before commit. This is what the GOV.UK patterns are built for |
| **Occasional** (monthly) | A report, a quarterly review | Recognition over recall. The user forgot the path since last time, the screen has to remind them |
| **Daily** (many times a day) | Working a queue, processing cases, triage | Speed and density. Keyboard paths, bulk actions, remembered filters and views, no confirmation for anything undoable. Guidance that helps the rare user slows this one down |

The same product often has all three: a recruiter screens applicants daily, sets up a job posting monthly, configures the pipeline once. Each gets its own brief.

## What to write down

One task per brief. Two tasks produce a screen that serves neither.

| Field | Rule |
|---|---|
| **Task** | Verb plus object, in the user's words. "Pick the five applicants to call this week", not "applicant management" |
| **User need** | "As a [role], I need [what], so that [why]". The *so that* is the part that decides between designs |
| **Trigger** | What happened just before. An email arrived, a deadline hit, a colleague asked. Never "opens the app" |
| **Routine** | How often (from the table above), what comes directly before and after, which other tools are open at the same time, what interrupts it |
| **User group** | Role, expertise in the domain, expertise with this software, device and setting (desk, shop floor, on the road), language (native or second language), relevant access needs |
| **Success criterion** | Observable evidence the task is done well. "Five applicants marked for a call within ten minutes, without opening each profile" is one. "Finds it intuitive" is not |
| **Today's workaround** | How it gets done now: a spreadsheet, a printout, a colleague who knows. The workaround shows what the software fails to do |
| **Constraints** | Legal, data protection, permissions, what the organisation cannot change |
| **Open assumptions** | Everything marked **(assumed)**, with who could confirm it |

Keep it under a page. A brief nobody rereads before designing is not a brief.

## Where it goes wrong

**The task is a feature in disguise.** "Filter applicants by status" is a solution. Ask what the filtered list is for, and write that down.

**The user group is a job title.** "Recruiters" hides that one works in a small agency on a laptop between calls and another works in a large HR department with two screens. Name the situation, not the title.

**The success criterion is a feeling.** Feelings cannot be checked in `ux-check` later. Replace every adjective with something someone could observe or count.

**Everyone is the user.** If the brief fits every role in the product, it was written for none of them.

## What this skill does not do

It does not design steps, screens or text. It does not run research; it writes down what research, tickets and people already know and marks the rest as assumed. It does not define a new product from nothing; that is product discovery, outside this collection.

## Where it sits

`ux-context` → `ux-flow` → screen (whatever builds screens in your setup) → `ux-text` → `ux-pattern` → `ux-check`

The brief is the input `ux-flow` checks for, and the success criterion is what `ux-check` measures the result against.
