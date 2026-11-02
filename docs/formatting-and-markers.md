# Formatting & Markers

How to format what you write in the module template so it reaches learners the way you meant it, and what each bracketed marker tells the converter to build. It applies to both templates, headings and tables. The few notes that hold for one template only are labeled <span class="tpl">Tables template</span> or <span class="tpl">Headings template</span>.

> The template guides: [Headings & paragraphs](module-template-headings.html) · [Tables](module-template-tables.html) · Problem lines in detail: [Problem Templates](problem-authoring-guide.html)

On this page

- [How the converter reads your document](#reads)
- [Text: bold, italics, lists, links](#text)
- [Pictures](#pictures)
- [Tables](#tables)
- [Math and science notation](#math)
- [The markers in square brackets](#markers)
- [Placeholders and square brackets of your own](#placeholders)
- [The labels](#labels)
- [What happens to a problem's lines](#problems)
- [Before you hand it off](#checklist)

---

## How the converter reads your document

The converter reads your document's structure, not how it looks. A line is a heading because it has a heading style, a list because it uses the list buttons, a problem because it has a `Problem Type:` line. Something that only *looks* right, like a line made big and bold, is ordinary text to the converter.

- **The outline comes from structure.** See the template guide for yours.
  - <span class="tpl">Headings template</span> Heading 1 is a section, Heading 2 a lecture or assignment, Heading 3 a page, and Heading 4 a heading inside that page.
  - <span class="tpl">Tables template</span> The shape of a row does that job, and Heading 4 marks a heading inside a cell.
- **Tracked changes count as accepted.** A deleted line is gone, and a moved one is where it was moved to. Hidden text is left out.
- **Some things are not read at all:** text boxes, footnotes and endnotes, charts, SmartArt, and embedded objects such as a Visio drawing or a MathType equation. The conversion report lists each one it finds. Type the text as ordinary paragraphs, and paste a chart or diagram as a picture.

## Text: bold, italics, lists, links

- **Bold and italics are kept**, in pages, questions, and answer choices alike. Use them for meaning: a key term in bold, a species or gene name in italics. Dropdown options are the exception. They cannot hold any formatting, so an option shows as plain text.
- **No custom fonts, sizes, or colors.** The platform sets the type. Text made bigger or colored to stand out loses that on the way in, and the checker reports it. Use a heading or bold instead.
- **A heading is a heading style.** Inside a page, use Heading 4 for a heading such as Overview or Key Takeaways. A bold line is not a heading to a screen reader.
- **Use the list buttons.** Numbers typed by hand (`1.`, `2.`) arrive as literal text, and the checker reports them. Indent a bullet with the list's own indent to nest it.
- **No empty lines for spacing.** The platform spaces paragraphs itself, and an empty paragraph is an extra gap that the checker reports.
- **A line break counts as a new paragraph.** Shift+Enter ends the line just as Enter does. That matters after a label: a line broken off under `Video File Name:` is page text, not part of the file name.
- **Paste without formatting.** Text copied from a website, a slide, or another document brings its fonts and colors with it, and the checker reports them. Paste with Ctrl+Shift+V (⌘+Shift+V on a Mac) to bring the words only.
- **Links are real links.** Use Insert › Link, and make the linked words say where it goes ("the MIT Climate Portal article on sea level"), not "click here".

## Pictures

Paste the picture where it should appear, and name and describe it with two lines just under it:

```
[the picture, pasted here]
File Name: Membrane_Receptor_Diagram
Alt Text: A receptor protein spanning the cell membrane, with a signal molecule bound to its outer end.
```

- **Alt text is required.** A learner using a screen reader gets nothing else. Describe what the picture shows that the text around it does not. A picture with no alt text gets a stand-in (`Diagram: NAME`), and the report lists it to fix.
- **The file name has no extension.** Leave out `: * ? " < > | #`, and do not use a folder name. Two pictures may not share a name.
- **The picture goes where its line puts it.** On a page, it follows the line it is pasted on. In an answer choice, paste it on the choice's line, and the choice shows the picture. In a problem's explanation, it shows inside Show Answer.
- **PNG or JPEG.** A diagram pasted from PowerPoint or Visio often arrives as EMF or WMF, which no browser shows. The report flags it; export the diagram as a PNG and paste that instead.
- **Size is set for you.** A wide diagram shows at up to 600 pixels, other pictures at up to 480, and every picture shrinks to fit a phone. You do not need to resize it in the document.

## Tables

A data table on a page is built as a table, with its header row and merged cells kept.

- **Bold the first row.** A bold first row becomes the table's column headings, which a screen reader announces with each cell.
- **Name the table with a `Caption:` line** just above it: `Caption: Enzyme activity at five temperatures`.
- **Merged cells are kept** as Word shows them, so a heading merged across two columns heads both.
- **Borders are not kept.** Tables are built without them, so do not use a border or a color to carry meaning.
- **Tables are for data, not layout.** Do not use a table to place text and a picture side by side.
- **Dropdowns can sit in a table** as a problem; see [Dropdown](problem-authoring-guide.html#3-dropdown).

<span class="tpl">Tables template</span> The whole module is already a table. A data table you insert inside a right-hand cell is read as a table after that cell's words.

## Math and science notation

Type math as MathJax between `\(` and `\)`, for example `\(2 \times 10^{-5}\)` or `\(H_2O\)`. Screen readers read MathJax correctly. Word's superscript and subscript formatting is not announced, so a screen reader can read 10<sup>-5</sup> as "10 minus 5".

Avoid Word's own equation editor. An equation built there arrives as a plain line of text (`p² + 2pq + q² = 1`), and one with a part a line cannot hold, such as a matrix, is reported instead of built. What to write as MathJax and what is fine as plain text is in [Accessible Math & Science Markup](math-markup.html).

## The markers in square brackets

A word in square brackets followed by a colon or by the closing bracket, such as `[TEXT]` or `[embed: …]`, is a marker: an instruction to the converter. Learners never see a marker. Square brackets with a slash inside are a dropdown, so `[Text/&Image]` is a dropdown, not a marker.

| Marker               | What it makes                                                                                                             | Where it goes                                                                                  |
|----------------------|------------------------------------------------------|---------------------------|
| `[TEXT]`             | A text component on a page with problems, so a passage or a picture shows on the page instead of in the problem before it | At the start of the first line of the text, after a problem's explanation                      |
| `[word cloud]`       | A word cloud: learners type a few words, then see everyone's                                                              | At the start of the prompt's line, usually the opening question before a lecture's first video |
| `[embed: https://…]` | Another site's page, such as a simulation, in a frame on the page                                                         | At the end of the line that names it                                                           |
| `(X)` and `(  )`     | The correct and the other choices of a multiple choice                                                                    | At the start of each answer choice                                                             |
| `[X]` and `[  ]`     | The correct and the other choices of a checkbox                                                                           | At the start of each answer choice                                                             |
| `[G1/&S/M]`          | A dropdown; `&` marks the correct option                                                                                  | In the sentence, where the dropdown appears                                                    |


### `[TEXT]`: text between problems

On a page with problems, every line after a problem is read as part of it, so a passage written there ends up in the explanation, behind Show Answer. Start the passage with `[TEXT]` and it shows on the page instead. When the passage has a title, give the title a Heading 4 instead of using `[TEXT]`. Either way, the text runs to the next problem, heading, or marker.

```
Explanation: …the end of the problem before it.
[TEXT] The council meets again in spring to review the plan.
Problem Type: multiple choice
…
```

<span class="tpl">Tables template</span> You can also give the text a row of its own under the problem, with the page's name cell merged down beside it. See [A page in several components](module-template-tables.html#components).

A page with no problems needs no `[TEXT]`: an overview or a summary is text already. Setup for the next question needs none either. Write it just above that question's `Problem Type:`, and it shows above the question.

### `[word cloud]`: the opening question

Write the marker, then the prompt, then the instructions, all on one line:

```
[word cloud] What comes to mind when you hear "climate"? Summarize your thoughts in three words or less. Submit up to three answers. After submission, you will see a word cloud of responses from everyone.
```

- **The prompt goes after the brackets, not inside them.** `[word cloud: What comes to mind?]` is not read as a word cloud. It is shown as written, and the conversion report says so.
- **"Submit up to three answers" sets the number of boxes.** Change the number there to change how many answers a learner gives.
- **Every word is yours.** The converter adds nothing, so the template's standard instructions stay as written unless you change them.

### `[embed: …]`: a page from another site

Put the address in the marker at the end of the line that names the page:

```
Membrane Transport simulation [embed: https://phet.colorado.edu/sims/html/membrane-transport/latest/membrane-transport_all.html]
```

- **The line's words name the frame.** They stay on the page above it, and a screen reader announces the frame by them, so make them say what the page is. A marker alone on its line takes the name of the heading above it, and the report says so.
- **Use the `https://` address.** A browser blocks an `http://` page inside the course.
- **YouTube and Vimeo links work as copied** from the address bar; they are turned into the site's player. Course lecture videos still use `Video File Name:`, which gives the player its transcript.
- **Not in a data table**, and not on the module's title. A frame does not fit there, so the marker is reported and not built.
- <span class="tpl">Tables template</span> A page's own right-hand cell is fine: that cell is the page, not a data table.
- **Try it in Studio.** The converter cannot tell whether a site allows its page in a frame, or whether that page works with a keyboard and a screen reader. The report lists every embedded page to check in Studio's preview.

A misspelled marker (`[embde: …]`), or one without its brackets, is named in the conversion report.

### Answer choices and dropdowns

`(X)`, `[X]`, and the dropdown's `[…/&…]` are covered in full in [Problem Templates](problem-authoring-guide.html). Two reminders:

- **Round brackets for one answer, square for several.** A checkbox needs `[X]` on every correct option.
- **Quote a dropdown option that has its own slash or brackets**: `[&"I/O Port Count"/Bandwidth]`. Without the quotes, the slash splits the option in two.

### Video files in brackets

The tables template writes a video's cell as `[video file]`. Either template reads these:

| You write                                   | What it does                                                                                                           |
|---------------------------------------------|---------------------------------------------------|
| `[video file: UCE_0023_S1]`                 | The same as `Video File Name: UCE_0023_S1`. A cell still reading `[video file]` is a video still waiting for its file. |
| `[transcript file: UCE_0023_S1_transcript]` | The same as `Transcript File Name:`                                                                                    |


### Notes for the platform team

When the platform team adds text for you, such as an article from the MIT Climate Portal, leave a note where it goes instead of pasting it in. The note is written differently in each template:

| Template | Write the note as                                                                                                                                                       |
|----------|-------------------------------|
| Tables   | `[Article: How Do We Know Climate Change Is Happening? https://climate.mit.edu/explainers/… The platform team pastes the article text here.]` alone in a row of its own |
| Headings | `<<The platform team pastes the article text here: How Do We Know Climate Change Is Happening? https://climate.mit.edu/explainers/…>>` alone on its line                |


- **Include the words "platform team".** That is how the note is told apart from template text you forgot to replace.
- **Learners never see the note.** Its place says "Content for this page is still in development" until the platform team pastes the text in Studio, and the conversion report lists it under Finish in Studio.
- <span class="tpl">Headings template</span> Do not write the note in square brackets. Square brackets are your own text there, so the note would be shown to learners.

## Placeholders and square brackets of your own

- **`<< >>` is template text to replace.** Delete the whole span, brackets and all, and write your own words. A line that is only a placeholder is left off the page and reported, so a forgotten one never reaches learners, but the page it was on is reported as unwritten.
- <span class="tpl">Tables template</span> Some placeholders are written in square brackets, such as `[Name of Video 1]`, and are read as placeholders.
- <span class="tpl">Headings template</span> Square brackets are always your own text, never a placeholder.
- **Square brackets of your own are kept.** A reference `[1]`, an interval `[0, 1]`, a citation `[IPCC, 2021]`, or `[sic]` shows as you wrote it.
- **A quotation in angle brackets** needs guillemets, `« »`. Typed as `<< >>`, it is taken for a placeholder.

## The labels

A label is a word or two and a colon at the start of a line: `Question:`, `Alt Text:`. The converter reads the label and uses what follows it. Learners never see the label itself.

- **Spell it as the template does.** A near miss (`Alt Txt:`, `Expanation:`) is not read as the label. The conversion report names it, so it can be fixed.
- **A hint in brackets is fine.** `Trailing label (if applicable):` and `Alt Text (required):` are read as the label.
- **Bold on a label does not matter.** A label is read whether or not it is bold.
- **Separate alternatives with semicolons.** `Also accept: mitotic division; mitosis`. A comma is read as part of one answer.

| For                 | Labels                                                                                                  |
|---------------------|------------------------------------|
| Every problem       | `Problem Type:` · `Title:` (optional, names the problem) · `Question:` · `Explanation:`                 |
| Choice problems     | `Answer choices:`                                                                                       |
| Typed answers       | `Correct answer:` · `Also accept:` · `Accepted range:` · `Trailing label:`                              |
| Open-ended          | `Grading:` · `Model answer:`                                                                            |
| Poll                | `Poll question:` · `Poll answers:` · `Feedback:` · `Show results to learners:` · `Submissions allowed:` |
| Drag and drop       | `Zones:` · `Items (drag to the correct zone):`                                                          |
| Videos              | `Video File Name:` · `Transcript File Name:`                                                            |
| Pictures and tables | `File Name:` · `Alt Text:` · `Caption:`                                                                 |


## What happens to a problem's lines

The full rules for each problem type are in [Problem Templates](problem-authoring-guide.html). These are the parts that surprise people.

### What ends up behind Show Answer

Learners see a problem's question and options before they answer, and its explanation only after. So everything written after the answer goes behind Show Answer:

- **A line between the answer and the explanation**, after the choices or after a typed key. It is shown first inside Show Answer, because on the page it could give the answer away. The same goes for a picture or a table written there.
- **Everything under the explanation**: every paragraph, list, picture, and table, up to the next heading, label, answer choice, or question. An explanation can run to several paragraphs, and all of them stay behind Show Answer.

To put something on the page after a problem, start it with `[TEXT]` or give it a Heading 4 (see [`[TEXT]`](#text-marker)). To show it before the question, write it just above `Problem Type:`.

### How a typed answer is read

For short answer:

- **A note in brackets after the answer is ignored.** `Correct answer: mitosis (case-insensitive)` accepts "mitosis". Case, surrounding spaces, and a final full stop never matter.
- **Keep the answer to a word or a short phrase.** An answer that is a whole sentence becomes a model answer that learners read. It is not graded, and the report says so.
- **Leave `Also accept:` off when there is nothing else to accept.** `Also accept: N/A` adds no answer.

For numerical input:

| You write             | It is read as                                                               |
|-----------------------|--------|
| `20 ± 2`              | 20, accepting 18 to 22                                                      |
| `86-90` or `86 to 90` | Any number from 86 to 90 (smaller number first)                             |
| `88%`                 | 88, with % shown after the answer box                                       |
| `25 mL`               | 25, with mL shown after the answer box                                      |
| `1,500`               | 1500                                                                        |
| `6.02 × 10^23`        | 6.02e23                                                                     |
| `$25`                 | 25\. Nothing can show before the box, so name the currency in the question. |


If you also give a `Trailing label:`, make it the same unit as the answer. A different unit turns the problem into a short answer, and the report says so.

### "All of the above" and "None of the above"

A multiple choice's options are shuffled for each learner, but an option about the others, "All of the above" or "None of the above", stays where you wrote it, after the rest. Write it last.

### Naming a problem with `Title:`

A problem takes its page's name. To give one problem its own name, write `Title:` just above its `Problem Type:`:

```
Title: Knowledge Check: Atmospheric Composition
Problem Type: multiple choice
Question: …
```

- **It names that one problem only.** The next problem, with no `Title:` of its own, takes the page's name again.
- **It replaces the heading's name** for that problem, in the course and in the Studio outline, and the report says so.
- **Setup between `Title:` and `Problem Type:`**, such as a passage, a picture, or a table, is shown above the question.

## Before you hand it off

- No `<< >>` left, except notes for the platform team.
- Every picture has a `File Name:` and an `Alt Text:` line.
- No text boxes, footnotes, or equations from Word's equation editor.
- Numbers and bullets come from the list buttons, not typed by hand.
- Every problem has its `Problem Type:` line and an explanation, except a poll.
- Text meant for the page after a problem starts with `[TEXT]` or a Heading 4.
- Every `[embed: …]` line names what it embeds, with an `https://` address.
- Tracked changes are accepted or rejected, so what you see is what is converted.
- The checker shows no errors, and you have looked at each warning.
