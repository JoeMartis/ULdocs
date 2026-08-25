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

## 3. Rules to build: a goals side to match the objectives side

> **Approved to build.** Faculty confirmed in August 2026 that they want these.
> Sections 3.1–3.6 are the ask; 3.7 lists what is worth doing in the same pass.

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

None of the six is a novel check. Each has a working lecture counterpart named
in its spec below, and five of the six are that counterpart pointed at a
different page.

### Where they live

The IDs below split the way the existing catalog does, where Lectures holds the
page-level checks and Learning Objectives holds the content of the list on it:

- **Module Overview** (new category) — the page exists and is formatted:
  `module-overview-*`, one rule here plus two in 3.7.
- **Learning Goals** (new category) — the goals list itself:
  `learning-goals-*`, four rules here plus the AI pair in 3.7.
- **Module Summary** (existing family of 3) — gains one rule.

**Locating a module overview** is the one piece these specs cannot supply:
`module-summary-exists` already resolves one end of a module, so apply the same
locator to the other end. Everything below assumes it returns a single unit per
module, and that a module with no such unit is detectable as absent rather than
as empty.

### Severity and defaults

Each severity below **matches its lecture counterpart**, so the same defect
carries the same weight whether it lands on a goal or an objective.

But **ship all six off**, and enable them per program after a baseline run. No
module has ever been checked on this axis. Switching `module-overview-present`
on at `error` across four programs would mark most modules not publish-ready
overnight — a true result, but not one anyone can act on in a sitting. Enable,
read the baseline, fix, then promote to on-by-default.

### 3.1 `module-overview-present` — Module Overview Present

`error` · static · ship off · mirrors `lectures-overview-present` (error, on)

Two failure modes, as in the counterpart, which checks both that the page
exists and that it carries objectives:

- Module has no overview unit → **"Module has no overview page."**
- Overview exists but carries no goals list → **"Module overview has no
  learning goals list."**

The second is the one that will actually fire. Detect it the way the
counterpart detects a missing objectives list: a list of two or more items in
the overview body, introduced by a recognised stem (see 3.2) or, absent a stem,
any such list.

### 3.2 `learning-goals-stem-format` — Goals Introductory Stem

`warning` · static · ship off · mirrors `learning-objectives-stem-format`
(warning, off)

Accepted stem, in the program's voice from §1 of this file:

- Universal Biology / Climate / Semiconductor: **"At the end of this module,
  you will be able to:"** — also accept *you should be able to*.
- Universal AI: **"At the end of this module, the learner will be able to:"**

Explicitly rejected: **"Our goals for this module are:"** and **"This module
covers…"**. The guide now frames goals neither around us nor around the
material.

Message: *Introduce the learning goals with "At the end of this module, you
will be able to:".* (Voice per program.)

⚠️ The objectives version of this rule **still accepts "Our goals for this ___
are:"** — see §4. Narrow both accepted lists in the same change, or this rule
will forbid on a module overview exactly what its sibling permits on a lecture
overview.

### 3.3 `learning-goals-vague-verbs` — Avoid Vague Goal Verbs

`warning` · static · ship off · mirrors `learning-objectives-vague-verbs`
(warning, off)

Reuse the counterpart's verb list unchanged — the guide names the same three
for both ("understand", "know", "be familiar with"), and both of its weak
examples open with a listed verb. Flag a goal bullet whose leading verb, after
any leading bold, is on that list.

- Fails: *Understand cell division.*
- Passes: *Explain how a cell's stage in the cycle determines whether it
  divides, repairs, or dies.*

Only the **message** differs from the counterpart, because the suggested
replacements sit at a different altitude: a goal's verb reaches across the whole
module — *explain, evaluate, connect, apply* — where an objective's points at
one markable thing — *calculate, label, predict, compare*.

### 3.4 `learning-goals-use-bullets` — Goals Use Bullet Points

`info` · static · ship off · mirrors `learning-objectives-use-bullets`
(info, off)

Flags a goals list marked up as a numbered list rather than bullets.
Message: *Learning goals should be a bullet list, not numbered.*

### 3.5 `learning-goals-bold-topics` — Bold Topics in Goals

`info` · static · ship off · mirrors `learning-objectives-bold-topics`
(info, on)

Flags a goals list whose key topic names are not bolded. **Match the
counterpart's threshold exactly** — whether it requires bolding per bullet or
per list, do the same here, so an author does not clear one bar on a lecture
and a different bar on a module.

### 3.6 `module-summary-takeaways` — Module Summary Key Takeaways

`warning` · static · ship off · mirrors `lectures-summary-takeaways`
(warning, on)

The cheapest of the six: the same rule, pointed at the module summary. The
label wording it already looks for — "takeaway", "key point/concept/term" — is
what the guide asks for on both lecture and module summaries, and the guide
states the same standard applies to both.

Message: *Module summary has no key takeaways list.*

### 3.7 Worth adding in the same pass

- **`module-overview-naming`** (`warning`, static) — the overview title reads
  `<Program>: <Module>`, e.g. "Universal Biology: Cell Biology", and does not
  open with a greeting ("Welcome to…"). This was the faculty's first point and
  nothing checks it today; the program list is already per-program config
  from §1.
- **`module-overview-bold-title`** (`warning`, static) — mirrors
  `lectures-overview-bold-title`. Note there is deliberately **no** module
  counterpart to `lectures-overview-bold-professor`: the guide asks for a
  bolded professor's name on lecture and recitation overviews only, since a
  module usually spans several lecturers.
- **`learning-goals-action-verbs`** and **`learning-goals-learner-centered`**
  (`warning`, ai) — the AI pair, mirroring `learning-objectives-action-verbs`
  and `learning-objectives-student-centered`. Hold these until the static rules
  have produced a baseline, and read §4 first: the student-centered prompt's
  calibration problem would be inherited wholesale.

### Out of scope, recorded so it is not lost

The guide asks that each goal have a matching takeaway — "If a lecture or
module has four, look for four takeaways." That is a genuinely new cross-page
check with no lecture counterpart to copy, so it is not part of this pass.

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
