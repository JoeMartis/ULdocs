# Content Authoring Guide

How to write course content in the template so the automated QA pass
stays quiet. This guide covers the **content you write and
format** — names, question wording, answer choices, explanations, objectives,
terminology, and clean formatting.

> Full rule catalog: [Rule Reference](rule-reference.html) · Attempts detail:
> [Attempts Policy](attempts-policy.html)

On this page

- [1. Writing style](#1-writing-style)
- [2. Overview and summary pages](#2-overview-summary-pages)
- [3. Lecture and video names](#3-lecture-video-names)
- [4. Problem names](#4-problem-names)
- [5. Question wording](#5-question-wording)
- [6. Answer options](#6-answer-options)
- [7. Problem explanations](#7-problem-explanations)
- [8. Formatting](#8-formatting)
- [9. Accessibility](#9-accessibility)
- [Appendix — Biology terminology](#appendix-biology-terminology)
- [Appendix — platform settings](#appendix-platform-settings-not-authoring)
- [Appendix — reference lists](#appendix-reference-lists)

---

## 1. Writing style

- **Address the reader as "you"** (or "learner(s)"), never "student" or "user".
- **No contractions** in instructional text — "do not", not "don't".
- **Active voice** and the **Oxford comma** — "DNA, RNA, and protein".
- **Define acronyms on first use** — spell it out the first time, then use the
  short form: "endoplasmic reticulum (ER)" first, "ER" after. Widely understood
  acronyms (DNA, RNA, PCR, ATP…) do not need defining.
- **Write literally for an international audience** — avoid US idioms and
  figurative phrasal verbs ("break a leg", "reach out", "a piece of cake"). If
  an idiom is unavoidable, define it (and consider defining it in the summary).
- **Put a space between a number and its unit** — "37 °C" not "37°C", "5 kg" not
  "5kg", "500 bp" not "500bp". Standard scientific notation always spaces the
  value from the unit symbol, degree symbol included.
- **Avoid ambiguous pronouns — especially "it".** In a science question a
  pronoun can point to more than one noun in the sentence, leaving the learner
  unsure of the referent. Name the noun instead: "the enzyme changes shape", not
  "it changes shape".

## 2. Overview and summary pages

- Each **module** gets an overview (with **learning goals**) and a module
  summary (with **key takeaways**).
- Each **lecture** gets an overview (with **learning objectives**) and a
  lecture summary (with **key takeaways**).
- Each **assignment** gets an overview and a summary page too (no takeaways
  required there).

**What makes a strong overview.** An overview orients the learner before they
dive in — it previews, it does not teach. The opening line differs by level: a
lecture uses **learning objectives** ("At the end of this lecture, you will be
able to:"); a module uses **learning goals** ("Our goals for this module
are:").

- **Bold the title** and **bold the professor's name**.
- **Frame it in a sentence or two**: what this lecture or module covers and
  why it matters, or how it connects to what came before. Do not summarize the
  whole thing here — that is what the objectives/goals list and the summary
  page are for.
- **Follow immediately with the objectives or goals list**, written like this:
- Start each one with a **measurable action verb** (Bloom's): "describe",
  "calculate", "predict", "compare" — not "understand", "know", "be familiar
  with".
- Frame around the **learner**: "you will be able to predict…", not "this
  lecture covers…".
- Use **bullet points**, not a numbered list, and **bold** the key topic
  names.
- **Keep it short.** A framing paragraph plus the list is enough — a long
  overview delays the learner from getting to the actual content.

**What makes strong key takeaways.** Key takeaways close the loop the overview
opened — each objective or goal promised should have a matching takeaway that
delivers on it. This applies to both lecture summaries and module summaries.

- **One takeaway per objective/goal.** If a lecture or module has four, look
  for four takeaways.
- **State the fact or skill, not the topic label.** "Mitosis produces two
  genetically identical diploid daughter cells" teaches something; "Mitosis"
  does not.
- **One sentence each**, as a bullet list — a takeaway is a fact to remember,
  not a paragraph to read.
- **Introduce nothing new.** A takeaway restates something already taught; it
  is not the place for a fact the learner has not seen yet.
- **Label the section clearly** — the QA tool looks for the word "takeaway" or
  "key point/concept/term" to confirm the list is there.

*Weak:* Mitosis · Meiosis · Chromosome number
*Strong:* Mitosis produces two genetically identical diploid daughter cells,
used for growth and repair. · Meiosis produces four genetically distinct
haploid gametes through two rounds of division. · Diploid cells carry two
copies of each chromosome; haploid cells carry one.

## 3. Lecture and video names

The Universal Learning Program does **not** number lectures.

**Naming lectures.** Name each lecture for the concept it covers, not its position
in the sequence:

- **5 words or fewer**, highlighting the key concept from the lesson — a short
  phrase, not a full sentence.
- **No numbers or symbols** — that includes Roman numerals ("II", "III"). Name
  the lecture for its content, not its position in a sequence.
- **Avoid jargon** — use words a learner already knows, not the technical term
  the lesson is about to teach.
- **Title case** — "Cellular Respiration", not "cellular respiration" or
  "CELLULAR RESPIRATION".
- **Unique within its module** — duplicate lecture names make the course
  outline confusing to scan.

**Naming videos.** A video's name flows directly into the name of every
knowledge check that follows it, so name it well from the start:

- **5 words or fewer**, highlighting the key concept from the lesson — a short
  phrase, not a full sentence. It has to read naturally inside "Knowledge
  Check: `<video name>`".
- **No numbers or symbols** — that includes Roman numerals ("II", "III"). Name
  the video for its content, not its position in a sequence.
- **Avoid jargon** — use words a learner already knows, not the technical term
  the lesson is about to teach.
- **Title case** — "Molecular Biology Experiment", not "molecular biology
  experiment" or "MOLECULAR BIOLOGY EXPERIMENT".
- **Unique within its module** — duplicate video names make the knowledge
  checks named after them collide.

**Follow each video with two or more knowledge checks.** Every video should have
at least two knowledge checks after it so learners can check their understanding.

## 4. Problem names

Both knowledge-check and assignment problems need a clear, specific title — never a
generic placeholder like `Question 1`.

**Naming Knowledge check problems.** A knowledge check takes the
name of the video that precedes it in the module:

- One knowledge check after a video → `Knowledge Check: <video name>`
  (e.g. `Knowledge Check: Molecular Biology Experiment`).
- Two or more after the same video → add an `A`/`B`/`C…` suffix:
  `Knowledge Check A: Molecular Biology Experiment`,
  `Knowledge Check B: Molecular Biology Experiment`.

**Naming assignment problems.** Title each problem for the question it asks,
not a generic label — e.g. `Transforming Data for Hill Coefficient
Calculations`, not `Question 1`.

- **Descriptive, not generic.** The title should tell the learner (and anyone
  scanning a list of titles) what the question is about.
- **Specific enough to be unique.** A title tied to the actual question
  content naturally will not collide with another problem's title the way a
  repeated "Question 1" would across different assignments.
- **Title case**, kept to a phrase — not a full restatement of the question.

## 5. Question wording

Write the expected instruction into the question text:

| Problem type | Include this instruction (exact wording) |
| --- | --- |
| Single-answer multiple choice | Select the best answer. |
| Checkbox (multi-answer) | Select all that apply. |
| Dropdown | Use the drop-down options to … *(finish with the question-specific ask)* |
| Numerical — whole number | Enter your answer as a whole number in the space provided. |
| Numerical — percentage | Enter your answer as a percentage with no rounding. Do not include the percent symbol in your response. |
| Numerical — decimal | Enter your answer as a decimal to two significant figures. |
| Open-ended auto-credit (one sentence) | Any thoughtful answer will receive credit; click the Show Answer button to check your thoughts. |

Pick the numerical phrase that matches the answer type.

## 6. Answer options

- Provide **at least two** choices, with **at least one correct**.
- **No duplicate** choices and **no blank** choices.
- Keep it to **4 choices or fewer** — five or more gets flagged to rewrite.
- **No letters or numbers labeling the choices** — enter just the option text.
  edX shuffles option order, so a hand-typed "A)" or "1." ends up on the wrong
  choice. Likewise in **explanations**, refer to a choice by its content, not by
  position ("option B", "the first choice").
- **Dropdowns:** the correct answer must **exactly match** one of the options —
  a stray space or typo makes no option correct.
- **Capitalization/punctuation:** options completing a fill-in-the-blank
  question start lowercase; standalone questions may start with a capital; add
  a terminal period only on full-sentence options.

## 7. Problem explanations

- **Every problem** needs a solution/explanation, **labeled** with the word
  "Explanation".

**What makes a strong explanation.** A strong explanation does not just tell the
learner the answer — it teaches the concept behind it.

- **Explains why, not just what** — give the reason the answer is correct, do not
  just assert it.
- **Provides reasoning or conceptual context** — connect the answer to the
  underlying principle.
- **Is substantive** — more than one sentence; a single sentence rarely teaches
  the concept.
- **Adds something new** — does not merely restate the question or repeat the
  correct option.
- **Addresses the wrong options** — for multiple-choice items, generally explain
  why the incorrect answers are incorrect, not just why the right one is right.
  In particular, address the misconception that makes each wrong option tempting.
- **Names options by content, not position** — never "Option 1", "the first
  option", or "choice B". Options may be shuffled when displayed, so a positional
  reference can point at the wrong answer.

## 8. Formatting

- **Do not paste rich text straight from Google Docs or ChatGPT** — it drags in
  hidden markup. Paste as plain text, then apply formatting in the template.
- **No custom font, size, or color** — let the platform's styling apply.
- **Bold** with the template's own bold formatting, not a colored/enlarged
  font. **Section headers** in overview/summary pages use Heading 4.
- **No empty paragraphs or empty components** (blank gaps). Do not nest
  paragraphs inside list items — use the template's list formatting.
- **Keep content responsive** — avoid fixed pixel widths on tables and images so
  it reflows on phones and tablets.
- *Monospace is sometimes used to display sequence data — if that gets flagged,
  review and dismiss it.*

## 9. Accessibility

- **Alt text** on every image — describe essential detail shown.
- **Meaningful link text** — the linked words indicate the destination.
- The **question text** should serve as the problem's label (the simple problem
  editor does this automatically).
- **Author math/science notation in MathJax** so screen readers read it
  correctly — exponents (`\(x^2\)`), scientific notation (`\(2 \times 10^{-5}\)`),
  **any** super/subscript (even a lone letter or an ion charge — HTML `<sup>`/
  `<sub>` is not announced by screen readers), and the multiplication sign
  (`\(2 \times 2\)`). Standalone Greek letters, relational operators (`≤ ≥ ≠ ±`),
  temperature degrees, and ordinals (`1st`) are fine in HTML. Full matrix:
  [Accessible Math & Science Markup](math-markup.html).

## Appendix — Biology terminology

Biology-specific terminology conventions — apply these only where the content covers biology.

- "PCR", not "PCR reaction" (the R already means "reaction"); same for
  qPCR/RT-PCR/ddPCR.
- "the active site of the protein", not the possessive "the protein's active
  site"; likewise "the position of the gene", "the structure of DNA".
- Introduce the method as "dideoxy (Sanger) sequencing" on first use.
- A **trait/phenotype** is dominant or recessive — an allele, gene, or mutation
  is not. "the dominant trait", not "the dominant allele".
- Italicize genus/species names, gene symbols, and restriction-enzyme prefixes;
  keep protein names upright.

---

## Appendix — platform settings (not authoring)

The QA tool also checks these, but they are configuration set during course
setup or as a platform settings field, not part of writing content. Hand them
to whoever owns course configuration. Full detail in the
[Attempts Policy](attempts-policy.html).

| Setting | Expected configuration |
| --- | --- |
| Problem attempts (`max_attempts`) | By problem type. Multiple choice 2; numerical — KC 5 / assignment 3; text — KC 5 / assignment 4; dropdown 1–2 by option count; checkbox (≤4) 2. |
| Show Answer | `after_all_attempts_or_correct` on every problem. |
| Grading weights | Homework 20%, Assignments 80%. |
| Course mode & dates | Self-paced; start date in the future; beta access 365 days early. |
| Discussions | Global Discussions tab hidden; none enabled in individual sections. |
| Video settings | Downloadable; non-empty edX video ID; unit title matches the video. |
| Transcripts | Present, downloadable, non-empty; speaker labeled "INSTRUCTOR". |
| AskTIM | Chat assistant enabled on relevant content (including objectives pages). |

---

## Appendix — reference lists

The curated word lists behind three of the checks. These are **editable per
program** — suggest additions or removals and we can adjust them.

**US idioms flagged** (Avoid US Idioms):
break a leg · reach out · piece of cake · hit the ground running · on the same
page · bite the bullet · cut corners · ball is in your court · under the weather
· call it a day · get the hang of · touch base · in a nutshell · rule of thumb ·
back to the drawing board · bottom line · up in the air · on the fence · wrap
your head around · run of the mill · off the top of · long story short · by and
large · in the loop · at the end of the day · the whole nine yards · rain check ·
raincheck · throw in the towel · the last straw · jump the gun · cut to the
chase · tip of the iceberg · ballpark · keep an eye on · down the road

**Acronyms NOT flagged** (Define Acronyms on First Use flags any acronym *not* on
this list):
DNA · RNA · ATP · ADP · AMP · NAD · NADP · FAD · PCR · US · USA · UK · ID · OK ·
TV · FAQ · URL · HTML · PDF · CPU · GPU · AI · AM · PM · CEO · FBI · NASA · MIT ·
PHD · BC · AD · EU · UN · WHO · HIV · AIDS · MRI

Also never flagged: common all-caps words that are not acronyms (TRUE, FALSE, YES,
NOTE, FYI, ETC, VS, EG, IE, NB, AKA, TBD, TODO, AND, OR, NOT, THE) and Roman
numerals (II, IV, VI, IX, XII, …).

**Units checked for number–unit spacing** ("5kg" → "5 kg"; the degree symbol is
always checked):
kg · mg · µg · ug · ng · mL · ml · µL · uL · dL · cm · mm · µm · um · nm · km ·
ms · µs · ns · mol · mmol · µmol · nmol · mM · µM · nM · pM · kHz · MHz · GHz ·
kPa · kJ · kcal · mV · mA · kDa · Da · bp · kb · rpm · min · hr · sec

Single-letter units (g, m, s, L, M) are intentionally excluded to avoid false
positives like "1990s".

**MathJax-only symbols** (flagged if used outside MathJax): ⊣ (the list is
extendable per program).
