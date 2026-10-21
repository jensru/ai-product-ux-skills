# AI Product UX Skills

**Skills for product and UX work in software that already exists.** Two skills, one workflow: design the steps and states of a task, then write the interface text for every one of those states.

Each skill is a folder with a `SKILL.md` that says what it is for, what it needs, what it produces, and how it is run. An agent such as Claude Code picks the skill by its description and does the work; the person decides.

by Jens Rusitschka, [kick & boost](https://kickboost.io/)

---

## The workflow

```
ux-flow  →  screen  →  ux-text
```

| Step | Skill | Produces |
|---|---|---|
| Design the steps | [ux-flow](skills/ux-flow/) | The task in six lines, a step table written as state changes, the decisions the brief forces (keyboard path, conflicts between users, where a workaround's data goes), a state catalogue per view (empty, loading, partial, error, no permission, success), a dead-end list |
| Build the screen | your own screen step | This collection does not build screens. Use whatever does that in your setup |
| Write the text | [ux-text](skills/ux-text/) | A handover developers can work down: assumptions, voice, a binding glossary, a replacement table with IDs and variables per element and state, the behaviour the text depends on, message patterns. With rules for German interfaces |

Nothing has to run in order. Each skill checks for its one precondition and says what it is building on. When the input is missing, `ux-flow` writes the task down itself and marks what is assumed; `ux-text` derives the states from the screen and lists the ones it assumed.

## Which skill do I need?

| Situation | Skill |
|---|---|
| A form or process has to be cut into steps | [ux-flow](skills/ux-flow/) |
| A ticket names a feature, nobody wrote down the task | [ux-flow](skills/ux-flow/) |
| Users get stuck and nobody can say in which state | [ux-flow](skills/ux-flow/) |
| The build only knows "loading, data, error" | [ux-flow](skills/ux-flow/) |
| Errors say "invalid input", empty states say "No data" | [ux-text](skills/ux-text/) |
| The same thing has three names across screens | [ux-text](skills/ux-text/) |
| A German interface reads like a translation | [ux-text](skills/ux-text/) |

## What the skills are built on

The skills do not invent design rules. They lean on two bodies of published, tested guidance and link to the source instead of copying it:

- **[GOV.UK Design System](https://design-system.service.gov.uk/)** and the [Service Manual](https://www.gov.uk/service-manual) for the structure of a task: one thing per page, question protocol, check answers before commit, error messages and error summary, validation, long tasks. Built for people who use a service rarely and must get it right the first time.
- **[Material Design 3](https://m3.material.io/)** and Android's navigation principles for movement and state: interaction states, undo after the fact, empty states, content design. Built for tools people use often.

The skills read both through one lens: **how often the user does this task**. Rare tasks get guidance, daily tasks get speed and density. Getting that wrong produces a screen that is correct and still wrong.

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
evals/README.md       How the skills were tested and what the runs showed
skills/
  ux-flow/SKILL.md
  ux-text/SKILL.md
```

## Status

October 2026. Both skills were tested blind against their previous versions on two invented cases from different domains (a dispatch tool used all day by experts, and an expense form used occasionally on the phone). The current versions were rated better in both cases: `ux-flow` mainly through complete states and decisions instead of open options, `ux-text` through a handover developers can apply directly. Neither has been run on a real product yet. Method, scores and what still goes wrong: [evals](evals/README.md).

Contributions: open an issue with the situation the skill got wrong. A skill changes because a run showed a gap, not because a rule sounded nicer.

## About

**Jens Rusitschka** is an interaction designer with over 20 years in product work and several years focused on prompt engineering, AI prototyping and agentic workflows.

[Website](https://kickboost.io/) | [LinkedIn](https://www.linkedin.com/in/jensru)

---

*AI Product UX Skills | Jens Rusitschka, kick & boost | 2026 | Licensed under [CC BY 4.0](LICENSE)*
