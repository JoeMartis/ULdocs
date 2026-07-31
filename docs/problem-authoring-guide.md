# Problem Templates

For each type below you will find: the exact instruction to include, the rules for
the answer options, and a **filled-in template example** showing exactly how to
write it.

> **Reading the template examples:** mark the one correct choice with `(X)`; mark
> every correct checkbox with `[X]`. In a dropdown, the options sit inline in
> brackets and the correct one is marked with `&` — e.g. `[G1/&S/M]`.

On this page

- [Problem names](#problem-names)
- [1. Multiple choice (single answer)](#1-multiple-choice-single-answer)
- [2. Checkbox (select all that apply)](#2-checkbox-select-all-that-apply)
- [3. Dropdown](#3-dropdown)
- [4. Numerical input](#4-numerical-input)
- [5. Text / short answer](#5-text-short-answer)
- [6. Open-ended, auto-credit](#6-open-ended-auto-credit-any-thoughtful-answer)
- [7. Drag and drop](#7-drag-and-drop)
- [Attempts quick reference](#attempts-quick-reference)

---

## Every problem — the shared checklist

These apply to **all** problem types:

- **Include the type-specific instruction** (see each type below), as the last
  sentence of the question.
- **Write an explanation** for every problem, labeled with the word
  "Explanation". See [Writing a strong explanation](#writing-a-strong-explanation)
  below for what the tool checks.
- **Answer options:** no hand-typed `A.` / `1.` labels on options (the options
  may shuffle); keep to **4 options or fewer**; no duplicate or blank options.
- **Notation:** math/science in MathJax; a space between a number and its unit
  ("37 °C"); no ambiguous "it"; follow the biology terminology rules.

---

## Problem names

**Knowledge-check naming:** a knowledge check is named after the video before it
— `Knowledge Check: <video name>`, or `Knowledge Check A/B: <video name>` when a
video has two or more.

**Naming assignment problems.** Title each problem for the question it asks,
not a generic label — e.g. `Transforming Data for Hill Coefficient
Calculations`, not `Question 1`.

- **Descriptive, not generic.** The title should tell the learner (and anyone
  scanning a list of titles) what the question is about.
- **Specific enough to be unique.** A title tied to the actual question
  content naturally will not collide with another problem's title the way a
  repeated "Question 1" would across different assignments.
- **Title case**, kept to a phrase — not a full restatement of the question.

---

## Writing a strong explanation

A strong explanation does not just tell the learner the answer — it teaches the
concept behind it. This tool gives instant feedback against the criteria below —
check your explanation with [Explain2Me](https://joemartis.github.io/Explain2Me/) —
so an explanation can be revised and re-checked until it is strong. Learners have a
chat companion for follow-ups, so an explanation need not cover every edge case,
but it must give a solid foundation.

- **Explains why, not just what** — give the reason the answer is correct; do not
  just assert it.
- **Provides reasoning or conceptual context** — connect the answer to the
  underlying principle.
- **Is substantive** — an explanation should be more than one sentence; a single
  sentence rarely teaches the concept.
- **Adds something new** — it does not merely restate the question or repeat the
  correct option.
- **Addresses the wrong options** — for multiple-choice items, generally explain
  why the incorrect answers are incorrect, not just why the right one is right. In
  particular, address any misconceptions learners may have — the misunderstanding
  that makes each wrong option tempting.
- **Names options by content, not position** — never say "Option 1", "the first
  option", or "choice B". Answer options may be shuffled when displayed, so a
  positional reference can point at the wrong answer.

---

## 1. Multiple choice (single answer)

- **Instruction:** end the question with **"Select the best answer."**
- **Options:** 2–4 choices; exactly **one** marked correct; no duplicates or
  blanks; no `A)`/`1.` labels.
- **Capitalization:** options start lowercase unless the option is a proper
  noun or a full sentence; add a terminal period only on full-sentence
  options.

**How to write it in the template:**

```
Question:  Which organelle produces most of the ATP in a cell? Select the best answer.
Answer choices (mark the one correct answer):
   (  ) the nucleus
   (X) the mitochondrion
   (  ) the ribosome
Explanation:  The mitochondrion is the site of oxidative phosphorylation, where
              the electron transport chain uses the energy from glucose breakdown
              to build most of the ATP in a cell — which is why the mitochondrion
              is often called the powerhouse of the cell. The nucleus is tempting
              because it holds the DNA of the cell, but storing genetic
              instructions is not the same as producing energy. The ribosome reads
              those instructions to build proteins and consumes ATP rather than
              producing it. Only the mitochondrion carries out the
              energy-generating reactions the question asks about.
```

## 2. Checkbox (select all that apply)

- **Instruction:** end the question with **"Select all that apply."**
- **Options:** at least 2, at least one correct; **4 or fewer** (5+ gets flagged
  to rewrite); no duplicates, blanks, or labels.

**How to write it in the template:**

```
Question:  Which of the following are purines? Select all that apply.
Answer choices (mark every correct answer):
   [X] adenine
   [X] guanine
   [  ] cytosine
   [  ] thymine
Explanation:  Purines have a two-ring (fused six- and five-membered) structure,
              and adenine and guanine are the two purines found in DNA — a handy
              way to remember the pairing is that the longer word "purines" goes
              with the larger, double-ring bases. Cytosine and thymine are
              pyrimidines: they have only a single six-membered ring, so they do
              not belong in this group. This size difference matters biologically,
              because a purine on one strand always pairs with a pyrimidine on the
              other, keeping the DNA double helix a uniform width.
```

## 3. Dropdown

Use a dropdown **only for a formatting reason** — to complete a statement inline,
fill cells in a table, or present a one-to-one match. If the question works as a
standalone pick-one question, author it as **Multiple Choice** instead: a multiple
choice lowers the cognitive load for the learner.

- **Instruction:** begin with **"Use the dropdown options to …"** (e.g. "…complete
  the following statements."); for a one-to-one match set, use **"Match the
  following."**
- **Writing the dropdown inline:** put the choices in brackets at the point in the
  statement where the dropdown appears, separate them with slashes, and mark the
  correct one with an **`&`** — for example `[G1/&S/M]`. You can place several
  dropdowns in one set of statements.
- **Options:** 4 or fewer per dropdown; no labels.

**How to write it in the template — in a statement:**

```
Question:  Use the dropdown options to match the phase of the cell cycle to the
           activity during that phase.
The cell grows and acquires nutrients during the [&G1/S/M] phase.
The cell replicates DNA during the [G1/&S/M] phase.
The cell divides into two during the [G1/S/&M] phase.
Explanation:  The cell cycle proceeds through G1, S, and M in order. During G1 the
              cell grows and takes in nutrients to prepare for division. During S
              phase — S stands for synthesis — the cell copies the entire genome so
              that each daughter cell receives a complete set of DNA. During M
              phase (mitosis) the duplicated chromosomes are separated and the cell
              divides into two. Matching each activity to the correct phase checks
              that the learner knows the order and the purpose of the phases, not
              just the names.
```

**Or, to place dropdowns in a table.** Use a table when each cell is an
*independent* choice — the options can repeat and there is no one-to-one pairing.
(If instead each item pairs one-to-one with a match from a shared list, use the
*one-to-one match* form below rather than a table.)

```
Question:  Use the dropdown options to complete the table.

Change to the reaction                            |  Effect on enzyme activity
Raise the temperature well above the optimum      |  [increase/&decrease/no change]
Add more substrate once the enzyme is saturated   |  [increase/decrease/&no change]
Add a competitive inhibitor                       |  [increase/&decrease/no change]
Explanation:  Above the optimal temperature the enzyme denatures and loses shape,
              so activity falls. Once every active site is already occupied, adding
              more substrate cannot speed the reaction, so activity does not change.
              A competitive inhibitor blocks active sites, so fewer reactions occur
              and activity falls. Each row is judged on its own and the same options
              can repeat, which is what makes this a table of independent choices
              rather than a one-to-one matching.
```

**Or, as a one-to-one match (matching).** Each item pairs with one match from a
shared list that appears under every item, with each match used once. List each
item with its correct match; **do not number or letter them** (the drop-down
choices may shuffle). Keep to **4 or fewer** pairs, and make every match distinct.

```
Question:  Match the following.
Items and their correct match:
   Mitochondrion   →   Produces most of the ATP in a cell
   Nucleus   →   Stores the DNA of the cell
   Ribosome   →   Builds proteins
   Golgi apparatus   →   Modifies and packages proteins for shipping
Drop-down choices (offered under every item):  Produces most of the ATP in a cell;
   Stores the DNA of the cell; Builds proteins; Modifies and packages proteins for
   shipping
Explanation:  The mitochondrion runs oxidative phosphorylation to make most of the
              ATP in a cell, so the mitochondrion is the powerhouse. The nucleus is
              the vault that stores the DNA of the cell, keeping the genetic
              instructions safe. The ribosome reads those instructions to build
              proteins. The Golgi apparatus then modifies and packages those
              proteins for shipping. Because every drop-down offers all four
              functions, the learner has to know each pairing rather than guess by
              elimination.
```

## 4. Numerical input

- **Instruction:** pick the phrase that matches the answer type:
- whole number → **"Enter your answer as a whole number in the space provided."**
- percentage → **"Enter your answer as a percentage with no rounding. Do not include the percent symbol in your response."**
- decimal → **"Enter your answer as a decimal to two significant figures."**
- **Accepted range — required whenever the answer is not a single exact value.**
  Give the tolerance or range so a correct measured or rounded answer is not
  marked wrong — e.g. `3.14 ± 0.01` or `3.1–3.2`. This is set in the problem but
  invisible on the page, and a missing range is a common source of wrongly graded
  answers in live courses. For a genuinely exact value (a count), say so.
- **Trailing label (if applicable)** — a unit or word shown right after the
  input box (e.g. `%`, or "red-eyed flies"), so the learner does not have to
  type it.

**How to write it in the template:**

```
Question:  How many chromosomes are in a typical human somatic cell? Enter your
           answer as a whole number in the space provided.
Correct answer:  46
Accepted range:  exact — 46 is a whole-number count (for a measured or rounded
                 answer, give a tolerance, e.g. 3.14 ± 0.01)
Trailing label (if applicable):  chromosomes
Explanation:  Somatic (body) cells are diploid, meaning they carry two copies of
              each chromosome — one inherited from each parent. Humans have 23
              distinct chromosome types, so two copies of each gives 23 pairs, or
              46 chromosomes in total. A common mistake is to answer 23, but that
              is the haploid number found only in gametes (eggs and sperm); those
              cells carry a single copy of each chromosome so that fertilization
              restores the full set of 46.
```

## 5. Text / short answer

- No special instruction phrase is required.
- **Correct answer:** give the accepted answer (matching is case-insensitive).
- **Alternative correct answers — give them whenever they exist.** List every
  acceptable variant (synonyms, spellings, abbreviations), e.g. accept both `DNA`
  and `deoxyribonucleic acid`. The problem can hold several accepted answers, but
  only the ones you supply are graded correct — a learner who types a correct
  synonym you left out is marked wrong.

**How to write it in the template:**

```
Question:  Name the type of cell division that produces two genetically identical
           daughter cells.
Correct answer:  mitosis   (case-insensitive)
Also accept:  mitotic division
Explanation:  Mitosis is the division that copies the genome once and splits the
              genome evenly into two daughter cells, each diploid and genetically
              identical to the parent — this is how the body grows and replaces
              worn-out cells. Students often confuse mitosis with meiosis, but
              meiosis includes two rounds of division and produces four haploid
              cells that are genetically distinct, which is exactly why meiosis is
              used to make gametes rather than to replace ordinary body cells.
```

## 6. Open-ended, auto-credit (any thoughtful answer)

The custom one-sentence type that auto-grades **any non-empty answer as
correct**, then shows the model answer.

- **Instruction:** the prompt must end with the exact phrase
  **"Any thoughtful answer will receive credit; click the Show Answer button to
  check your thoughts."**

**How to write it in the template:**

```
Question:  In one sentence, predict what would happen to translation if a cell ran
           out of tRNA. Any thoughtful answer will receive credit; click the Show
           Answer button to check your thoughts.
Grading:  any non-empty answer is marked correct.
Model answer (shown after the learner answers):  tRNA is the adapter that reads
           each mRNA codon and delivers the matching amino acid to the ribosome.
           Without tRNA, the ribosome would have no way to bring in the next amino
           acid, so the growing polypeptide chain could not be extended and
           translation would stall — protein synthesis would effectively stop even
           though the mRNA and ribosome are still present.
```

## 7. Drag and drop

A `drag-and-drop-v2` problem where learners sort items into named zones.
**Write the content below in the template; the build team creates the
drag-and-drop block in Studio from it.** The parser does not yet recognize
this block type (see [Attempts Policy](attempts-policy.html)), so
nothing here is auto-checked yet.

- **Instruction:** state directly what to sort and into what — e.g. "Drag
  each item to the zone it belongs in," or phrasing specific to the categories
  (e.g. "Place each statement under the process it describes.").
- **Zones:** name each zone with a short label — these become the drop
  targets. A zone also needs a plain-language description for screen readers;
  reusing the zone's label is fine unless the zone needs more context.
- **Items:** list each draggable item with the zone it belongs in. An item
  can belong to more than one zone if more than one answer is accepted for it,
  though most problems use a one-to-one mapping.
- **Mode:** we build these in **Assessment mode** — the learner places every
  item, then submits, and only then finds out what is correct (matching the
  attempt limits in [Attempts Policy](attempts-policy.html)). Standard
  mode instead gives unlimited tries with instant right/wrong feedback per
  drop; flag it if a problem should work that way instead.
- **Explanation:** one paragraph covering the overall reasoning, as with
  other problem types — the build team derives each item's individual
  correct/incorrect feedback text (shown when it is dropped) from your zone
  mapping, so you do not need to write those separately. The generic
  before-you-start and completion messages are also filled in by the build
  team unless you want something more specific.

**How to write it in the template:**

```
Question:  Place each statement under the type of cell division it describes:
           Mitosis or Meiosis.
Zones:
   Zone 1: Mitosis
   Zone 2: Meiosis
Items (drag to the correct zone):
   Produces two genetically identical diploid daughter cells. → Zone 1
   Produces four genetically distinct haploid gametes. → Zone 2
   Used for growth and tissue repair. → Zone 1
   Involves two rounds of division. → Zone 2
   Occurs in nearly all body cells. → Zone 1
   Occurs only in the cells that produce eggs or sperm. → Zone 2
Explanation:  Mitosis copies the genome once and splits it evenly into two
              daughter cells identical to the parent, which is how the body
              grows and replaces worn-out cells. Meiosis instead runs two
              rounds of division, producing four haploid cells that are
              genetically distinct from one another and from the parent —
              which is why meiosis is restricted to the cells that become
              gametes rather than ordinary body cells.
```

---

## Attempts quick reference

| Problem type | Options | Knowledge Check | Assignment |
| --- | --- | --- | --- |
| Multiple choice (single answer) | any | 2 | 2 |
| Multiple choice — problem bank | exactly 2 | 2 | 1 |
| Checkbox | ≤ 4 | 3 | 3 |
| Dropdown — one dropdown | 2 choices | 1 | 1 |
| Dropdown — one dropdown | 3–4 choices | 2 | 2 |
| Dropdown — 2–4 dropdowns | any | 2 | 2 |
| Any choice type | 5 or more | *rewrite* | *rewrite* |
| Numerical input | — | 5 | 3 |
| Text / short answer | — | 5 | 4 |
| Drag and drop | 2–4 items | 3 | 2 |
| Drag and drop | 5–6 items | 4 | 3 |
| Drag and drop | 7–8 items | 5 | 4 |
| Drag and drop | 9+ items | *split* | *split* |
| Open response, ungraded (ORA) | — | 2 | — |

This is an exact-match check — too few attempts is flagged just like too many.

A dropdown problem is counted like a checkbox, by its **number of dropdowns**: one
dropdown follows the choice-count rule above; 2–4 dropdowns get 2 attempts; a
problem with 5 or more dropdowns should be split into more than one problem. A
one-to-one match set is several drop-downs and follows the same counts.

A drag-and-drop problem is counted by its **number of draggable items** — more
items means more chances to place one wrong. A problem with 9 or more items
should be split into more than one problem rather than given more attempts. A
**strict one-to-one match** (every zone used exactly once, no repeats) gets
**one additional attempt** at every tier, since there is no elimination
benefit the way there is when zones repeat.

**Drag and drop and Open response (ORA)** are not yet parsed by the checking
tool, so their attempt counts above are the target policy but are **not yet
enforced**.
