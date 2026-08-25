# QA rule requests

Changes needed in the **QA tool**, not in these guides. Raised by the faculty
review of the Content Authoring Guide (August 2026) and recorded here so they
are tracked rather than living in a chat thread.

Every rule ID, severity and default below is quoted from
[Rule Reference](rule-reference.html) as it stands today.

> **Not authoring guidance.** This file is deliberately not linked from
> `index.html` and has no generated HTML page. If `build_guide_html.py` globs
> `docs/*.md`, exclude this file or it will produce an orphan page on the site.

## 1. Per-program configuration

Universal AI follows a different convention from Universal Biology, Universal
Climate and Universal Semiconductor Manufacturing on lecture names, knowledge
check names, assignment question numbering and voice. Confirmed by faculty. The
guide now documents both variants; the rules still enforce the UAI variant
everywhere.

| Rule | Today | Should be |
| --- | --- | --- |
| `lectures-naming` — requires `L X.Y` | warning, on for all | Universal AI only |
| `knowledge-checks-naming` — requires `Knowledge Check: Question N` | error, on for all | Universal AI only |
| `knowledge-checks-video-name` — the `Knowledge Check (A/B): <video name>` convention | warning, off | on for the other three programs |
| `assignments-question-numbering` — requires `Question 1`…`Question N` | error, on for all | Universal AI only |
| `terms-learner-not-student` — wants "learner", flags second-person "you" | warning, on for all | Universal AI only |
| `bio-address-as-you` — wants "you" | info, off | on for the other three programs |

Two things to settle while making these changes:

- **The severities are asymmetric.** Each UAI variant is an `error` or
  `warning`; each non-UAI counterpart is a `warning` or `info`. If both
  conventions are equally required, they should carry equal weight.
- **`knowledge-checks-sequential-numbering`** (error, on) verifies knowledge
  checks are numbered sequentially across a module. Outside Universal AI they
  are named after their video and carry `A`/`B` suffixes rather than numbers,
  so this looks like it should also be Universal AI only — needs confirming.

## 2. Rules to enable

These exist and are switched off. Enabling them improves the **lecture /
objectives** side only — see section 3 for why they cannot cover goals.

| Rule | Severity | Type | Catches |
| --- | --- | --- | --- |
| `learning-objectives-vague-verbs` | warning | static | "understand", "know", "be familiar with" |
| `learning-objectives-action-verbs` | warning | ai | the same, judged by model |
| `learning-objectives-student-centered` | warning | ai | objectives framed around the material rather than the learner |
| `learning-objectives-stem-format` | warning | static | a missing or non-standard introductory stem |
| `learning-objectives-use-bullets` | info | static | a numbered list where a bullet list is wanted |

## 3. Rules to build: mirror the lecture family onto modules

**Modules have goals; lectures have objectives.** Goals therefore appear only
on a module overview — and there is no module-overview rule of any kind, so the
Learning Objectives family can never reach them. This is the half of the gap
that configuration cannot close.

The asymmetry in the catalog: **Lectures (9) + Learning Objectives (7) = 16
rules**, against a **Module Summary family of 3** — summary exists, feedback
form link, dashboard link. None of the three looks at content, and there is no
Module Overview category at all.

So a module can ship today with no overview, no goals, and a summary with no
takeaways, and the QA pass reports nothing.

None of these is a novel check. Each has a working lecture counterpart to copy:

| Needed for modules | Copy from | Counterpart's severity |
| --- | --- | --- |
| Module overview exists, carrying learning goals | `lectures-overview-present` | error, on |
| Goals avoid vague verbs | `learning-objectives-vague-verbs` | warning, off |
| Goals use the learner-outcome stem | `learning-objectives-stem-format` | warning, off |
| Goals are a bullet list | `learning-objectives-use-bullets` | info, off |
| Key topics in goals are bolded | `learning-objectives-bold-topics` | info, on |
| Module summary carries key takeaways | `lectures-summary-takeaways` | warning, on |

## 4. Calibrate before enabling

- **`learning-objectives-stem-format` still accepts "Our goals for this ___
  are:"**, which the guide now forbids in favour of "At the end of this ___,
  you will be able to:". Enabling the rule as it stands permits both rather
  than enforcing the new wording. Narrow the accepted list at the same time.
- **`learning-objectives-student-centered` describes correct framing as "what
  the learner will be able to do" but illustrates it with "students will be
  able to …"** — wording the guide bans outright. The intent matches the guide;
  the illustration suggests the prompt may be calibrated on third-person
  "students". Run it against a real non-UAI objective written as "you will be
  able to…" before trusting it.

## 5. Defect in the Rule Reference itself

Its headline counts do not match its own tables. Counting the 133 rule rows:

| | Stated | Actual |
| --- | --- | --- |
| On by default | 103 | 102 |
| Off by default | 30 | 31 |
| Auto-fix | 19 | 18 |

If that file is generated from the tool's rule registry, the generator has an
off-by-one; if the counts are maintained by hand, they have drifted.
