# Evals

How the skills were tested, what the runs showed, and what still goes wrong. A skill changes because a run showed a gap; this file is where the runs are recorded.

[← README](../README.md)

---

## Method

- **Two invented cases** from different domains, chosen to differ in routine:
  - **Dispatch:** a work list in building-services software, used all morning by four expert dispatchers (daily, dense, two people on the same data, a legal qualification rule, a spreadsheet kept next to the tool).
  - **Expense claim:** a travel expense form in an HR self-service portal, used occasionally by a mixed workforce, mostly on the phone, some in a second language, some with a screen reader.
- The dispatch case was used to sharpen the skills. The expense case was written before the changes and not looked at while changing them; it is the holdout.
- Each case has a deliberately flawed screen with a list of planted problems (24 and 29 items), used as the answer key for text and review tasks.
- Every run is a fresh agent with only the input files and, depending on the condition, one skill. No human answers questions during the run.
- Results are anonymised and judged **blind** by a separate agent, with length explicitly not counted as merit. Rounds 1 and 2: one judge per case, five criteria scored 1 to 5 (25 maximum). Round 3: two judges per case, six criteria (30 maximum), the sixth being whether the result could sit unchanged in another product.

## ux-flow

Three versions so far. The first was built on GOV.UK and Material as the main source. The second added a checklist of decisions the brief forces (keyboard path, conflicts between users, where a spreadsheet's data goes). The current third version is the author's own method: every flow is an onboarding to the user's goal, each step written as before, during and after, acknowledged as lightly as possible, never answered from a menu of patterns.

**Flow documents, judged blind** (25 points in rounds 1 and 2, 30 in round 3 with "could this flow sit unchanged in another product?" added as a criterion; round 3 had two judges per case and two runs of the current version):

| Round | Case | Without skill | First | Second | Current |
|---|---|---|---|---|---|
| 1 | Dispatch | 20 | 22 | | |
| 2 | Dispatch | | 17 | 22 | |
| 2 | Expense claim (holdout) | | 19 | 21 | |
| 3 | Dispatch | | | 27 / 26 | 25 / 24 and 26 / 26 |
| 3 | Expense claim (holdout) | | | 27 / 26 | 25 / 25 and 23 / 21 |

As documents, the second version scored slightly higher: judges rewarded its technical decisions. The current version scored higher on guidance to the goal and on proportion, lower on "could a developer start without a meeting". That criterion turned out to be the wrong one for a concept: technical detail is the build plan's job, not the concept's (see below).

**Built into prototypes** (expense claim, same brief, same old form, same build constraints, judged blind on six criteria, 30 points):

| | Current ux-flow, ux-text, ux-build-plan | Second ux-flow, ux-text | Without skill |
|---|---|---|---|
| Task in five minutes on a phone | **5** | 3 | 4 |
| Way to the goal and the moment it pays off | **5** | 3 | 4 |
| States and errors | **5** | **5** | 4 |
| Text | 4 | 4 | 4 |
| Proportion (too much counts against) | 3 | 2 | **4** |
| Product-specific | **5** | 4 | 3 |
| **Total** | **27** | 21 | 23 |
| Agent time, all steps | about 22 min | about 35 min | about 10 min |

**What works**

- The current concept thinks from the goal: it takes the trip over from the travel request, reads amount and date from receipt photos so the user only confirms, and shows a running total from the first step as proof that the product calculates. None of this was asked for; it follows from "every step has a visible effect, fast to the goal". The second version had no receipt reading.
- A completeness check before submitting catches exactly the gaps for which a third of claims were sent back.
- Lighter acknowledgement: the change itself confirms the step, not a toast. From the dispatch flow: "the order moving into the technician's day is the acknowledgement".

**What still goes wrong**

- The current version still overbuilds in breadth (mileage, collecting receipts during the trip, notifications), though less than the second version, which had over a hundred states.
- Two runs of the same version on the same case differed by two to four points: the skill's output varies more than the judging does.

## ux-build-plan and ux-validate

New in round 3, tested once in the end-to-end run above. The build plan traced every item to a concept step, marked what it added, and sent four questions back to the concept instead of quietly changing it. The validation found that plan and prototype delivered the concept almost completely, and named the first fix: the running total was missing on the camera and check screens, so the payoff moment came one receipt late.

## ux-text

| Round | Case | Without skill | Previous skill | Older private skill with handover format | Current skill |
|---|---|---|---|---|---|
| 1 | Dispatch | 21 | 16 | 22 | |
| 2 | Dispatch | | 15 | 19 | **23** |
| 2 | Expense claim (holdout) | | 17 | 18 | **22** |

The first version of `ux-text` scored below running without a skill. The current version combines its GOV.UK rules with the handover format of an older private skill and replaces it.

**What works**

- A handover developers can work down without asking: stable IDs per element and state, final strings with defined variables instead of example values, a binding glossary the strings actually follow, and a behaviour table that links each needed change to the text IDs that depend on it.
- Full state coverage, including states the screen does not show yet (load error, conflict between two users, delete, failed actions with retry).
- Text and flow kept apart: an inverted confirmation (asking before a reversible action, not before an irreversible one) was recognised as a flow problem and solved there, not reworded.
- Voice from the routine: short strings for experts, plain language for an occasional and mixed audience.

**What went wrong before, and is fixed**

- The first version renamed terms users already use ("technician" to "person responsible", in a German interface) in the name of inclusive language. The rule now keeps existing role and domain names.
- It wrote strings with example data, spread over prose sections, and explained GOV.UK rules that did not apply.

**What still goes wrong**

- System error texts sometimes state a cause or a reassurance the product cannot know ("the connection was interrupted", "your data is not affected").
- Occasional over-explaining for experts in empty states.

## What was not kept

Three more skills were written and tested in the first round and taken out of this collection: a context brief skill (barely better than no skill; the user's goal and trigger now open `ux-flow`), a pattern skill (level with no skill), and a combined accessibility and usability review (strong on correct WCAG levels, but splitting it into two reports made the result worse, so it needs more work before it is published).

## Further testing needed

- **What ux-text adds to a build.** In the prototypes, ux-text always ran together with ux-flow, and all three prototypes got the same text score. It has been tested on its own as a text task, not isolated inside a build. Next: the same concept built once with and once without the text handover.
- **With a design system.** Every prototype so far was built from scratch in plain HTML. With an existing design system the build plan maps concept steps to existing components, which should cut build time; whether quality holds is unmeasured.
- **Method or hand-over.** In the end-to-end run, the new concept method and the separate build plan were new at the same time. The receipt reading and the running total come from the concept; the restraint in the build probably comes from the build plan's "nothing extra" rule. The two effects were not separated.
- **Separate agents.** The roles were run as separate agents with only their inputs. What happens when one agent runs all four skills in one context is untested.
- **More runs, more cases, a real product.** One end-to-end run, two invented cases, no real product.

## Limits

Mostly one run per condition. The same text by the first `ux-flow` scored 22 with one judge and 17 with another; in round 3 two judges on the same text stayed within two points of each other, but two runs of the same skill differed by up to four. Only results that point the same way on both cases are treated as findings here. Judges are agents from the same model family as the skills' users, which tends to reward completeness; the product-specific criterion was added in round 3 to counter that.

---

[← README](../README.md)
