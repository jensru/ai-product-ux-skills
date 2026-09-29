# AI Product UX Skills

**Skills for product and UX work in software that already exists.** Five skills, one workflow: pin down the task, design the steps and states, write the interface text, turn recurring answers into patterns, check the result against WCAG and a named heuristic set.

Each skill is a folder with a `SKILL.md` that says what it is for, what it needs, what it produces, and how it is run. An agent such as Claude Code picks the skill by its description and does the work; the person decides.

by Jens Rusitschka, [kick & boost](https://kickboost.io/)

---

## The workflow

```
ux-context  →  ux-flow  →  screen  →  ux-text  →  ux-pattern  →  ux-check
```

| Step | Skill | Produces |
|---|---|---|
| Understand the task | [ux-context](skills/ux-context/) | A context brief of half a page: task in the user's words, trigger, routine (rare, occasional, daily), user group, an observable success criterion, today's workaround, open assumptions |
| Design the steps | [ux-flow](skills/ux-flow/) | A step table written as state changes, one thing per step, a state catalogue per view (empty, loading, partial, error, no permission, success), a dead-end list |
| Build the screen | your own screen step | This collection does not build screens. Use whatever does that in your setup |
| Write the text | [ux-text](skills/ux-text/) | Labels, buttons, hints, error messages with an error summary, empty states, per element and state, plus a glossary and one line of reasoning per change. With rules for German interfaces |
| Fix it for every screen | [ux-pattern](skills/ux-pattern/) | One pattern file in the project's library, with source, states, accessibility, text and a status of "to test" or "decided" |
| Check the result | [ux-check](skills/ux-check/) | One report: WCAG 2.1 AA pass, a usability pass against ISO 9241-110:2020 or Nielsen's heuristics, optional visual critique, findings ranked by severity with criterion, location and fix |

Nothing has to run in order. Every skill checks for its one precondition, says what it is building on, and offers to run the skill before it when the input is missing. A skill that is told to go ahead anyway does, and writes its assumptions into the result.

## Which skill do I need?

| Situation | Skill |
|---|---|
| A ticket names a feature, nobody wrote down the task | [ux-context](skills/ux-context/) |
| The same screen gets redesigned twice because nobody agreed what it is for | [ux-context](skills/ux-context/) |
| A form or process has to be cut into steps | [ux-flow](skills/ux-flow/) |
| Users get stuck and nobody can say in which state | [ux-flow](skills/ux-flow/) |
| The build only knows "loading, data, error" | [ux-flow](skills/ux-flow/) |
| Errors say "invalid input", empty states say "No data" | [ux-text](skills/ux-text/) |
| A German interface reads like a translation | [ux-text](skills/ux-text/) |
| The library has no answer, every screen improvises | [ux-pattern](skills/ux-pattern/) |
| A review finding keeps coming back on new screens | [ux-pattern](skills/ux-pattern/) |
| Is this accessible and usable, before handoff or for a tender | [ux-check](skills/ux-check/) |

## What the skills are built on

The skills do not invent design rules. They lean on two bodies of published, tested guidance and link to the source instead of copying it:

- **[GOV.UK Design System](https://design-system.service.gov.uk/)** and the [Service Manual](https://www.gov.uk/service-manual) for the structure of a task: one thing per page, question protocol, check answers before commit, error messages and error summary, validation, long tasks. Built for people who use a service rarely and must get it right the first time.
- **[Material Design 3](https://m3.material.io/)** and Android's navigation principles for movement and state: interaction states, undo after the fact, empty states, content design. Built for tools people use often.

The skills read both through one lens: **how often the user does this task**. Rare tasks get guidance, daily tasks get speed and density. Getting that wrong produces a screen that is correct and still wrong.

Accessibility is checked against **WCAG 2.1 level AA**, the level EN 301 549 and most European accessibility laws point to. WCAG 2.2 additions are listed as an optional block.

## Install

**Claude Code.** Copy a skill folder into `.claude/skills/` in your project, or into `~/.claude/skills/` to have it everywhere. Claude Code picks the skill up by its `description`.

```bash
git clone https://github.com/jensru/ai-product-ux-skills.git
cp -R ai-product-ux-skills/skills/ux-* ~/.claude/skills/
```

Or symlink the folders, so a `git pull` updates them:

```bash
for s in ai-product-ux-skills/skills/ux-*; do ln -s "$PWD/$s" ~/.claude/skills/; done
```

**Other agents.** Point the agent at the `SKILL.md`. It is plain Markdown and works pasted into any chat model. Each skill is self-contained: everything it needs lives in its own folder, and skills refer to each other by name, never by path.

## Structure

```
README.md             This file
AGENTS.md             Conventions for writing and changing skills
LICENSE               CC BY 4.0
skills/
  ux-context/SKILL.md
  ux-flow/SKILL.md
  ux-text/SKILL.md
  ux-pattern/SKILL.md
  ux-check/SKILL.md
  ux-check/references/wcag-21-aa.md    All WCAG 2.1 A and AA criteria as a checklist
  ux-check/references/heuristics.md    ISO 9241-110:2020 and Nielsen, one line each
```

## Status

First public release, September 2026. The five skills were written from method, published guidance and earlier private skills, and none of them has been run end to end on a real product yet. Expect the wording of triggers and the step tables to change once they have. What is deliberately missing: a library of ready-made patterns. `ux-pattern` describes how a pattern is written when a gap shows up in real work, not a stock of patterns written on speculation.

Contributions: open an issue with the situation the skill got wrong. A skill changes because a run showed a gap, not because a rule sounded nicer.

## About

**Jens Rusitschka** is an interaction designer with over 20 years in product work and several years focused on prompt engineering, AI prototyping and agentic workflows.

[Website](https://kickboost.io/) | [LinkedIn](https://www.linkedin.com/in/jensru)

---

*AI Product UX Skills | Jens Rusitschka, kick & boost | 2026 | Licensed under [CC BY 4.0](LICENSE)*
