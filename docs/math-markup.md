# Accessible Math & Science Markup

Guidance from the MITx accessibility team on how to author math and science
notation so screen readers read it correctly. The
[`accessibility-math-mathjax`](rule-reference.html#accessibility) rule enforces the
high-confidence parts of this automatically (see *What the rule flags* below).

Questions about a specific case: mitx-access@mit.edu.

## When to use MathJax vs. HTML

| Notation | Author it as | Example | Notes |
| --- | --- | --- | --- |
| Math equation (inline) | MathJax | `\( \frac{y+4}{5}=1 \)` | Also for answer choices. `[mathjaxinline]…[/mathjaxinline]` works too. |
| Math expression / formula | MathJax | `\(2x+1\)` |  |
| Exponents | MathJax | `\(x^2\)` | Multi-character exponents use `{}`: `\(x^{n+1}\)`. |
| Scientific notation | MathJax | `\(2 \times 10^{-5}\)` |  |
| Chemical formulas / ions | MathJax | `\(H_2 O\)`, `\(Mg^{2+}\)` | mhchem extension is **not** currently enabled. Learners may need to be told chemistry is present. |
| Greek letters | HTML if **standalone**; MathJax if part of an expression | `&mu;` alone; `\(\mu = \frac{f}{n}\)` | GUI: "special character" menu. Raw HTML: entity code. |
| Notation that looks like math but isn't (e.g. genetics) | MathJax | `a \(\frac{bcd^-}{bcd^-}\) male fly` | Reads as a fraction; best available option for now. |
| Temperature degrees | Special symbol / HTML entity — **not** MathJax | `37 &deg; C` or `37 &#8451;` | `&deg;` reads "37 degree C"; `&#8451;` reads "37 degrees Celsius". Kelvin `&#8490;`. |
| Word/letter super- or subscript, **alone** | HTML | `para <sup>T S</sup>`, `m<sup>n</sup>` | Reads "para superscript TS", "m superscript n". |
| Word/letter super- or subscript, **in a longer string / context** | MathJax | `\(+/m^n\)`, `\(\frac{m^n}{m^n}\)` | Bends screen-reader rules, but no better option today. |
| Special symbols that only read aloud in MathJax | MathJax | `\(\dashv\)` | e.g. the "Left Tack" ⊣ reads only when in MathJax. List is growing. |

## What the rule flags

`accessibility-math-mathjax` (Accessibility, warning; off by default, on for
UBio) flags, **only outside existing MathJax**, the high-confidence cases:

- caret exponents (`x^2`, `10^-5`) and scientific notation (`2 × 10^-5`)
- unicode and HTML super/subscripts — **including lone letters and charges**
  (`cm²`, `mⁿ`, `H<sub>2</sub>O`, `Cl<sup>-</sup>`). The accessibility team's
  screen-reader testing found HTML super/subscripts are **not announced at all**
  ("mⁿ" reads "m n", "Cl⁻" drops the charge), so all of them need MathJax.
  Ordinal suffixes (`1st`, `2nd`, `3rd`, `4th`) are exempt.
- the **multiplication sign `×`** — screen readers read it as the letter "x",
  not "times"
- symbols on the MathJax-only list (extend via `params.specialSymbols`)
- **plain-text chemical formulas and ions** (`H2O`, `C6H12O6`, `Mg2+`) — only
  when `params.flagChemistry` is true (on for UBio). Candidate tokens are
  validated against the real element-symbol set, so non-chemistry look-alikes
  (`COVID19`, `G2` phase, `T4` phage, an `A+` grade) are not flagged. Note the
  mhchem MathJax extension is not currently enabled.

It deliberately does **not** flag (confirmed to read correctly in HTML by the
accessibility team's screen-reader testing):

- **relational operators** `≤ ≥ ≠ ± ≈` (read as "less than or equal to", etc.)
- **standalone Greek letters** (`μ`, `Δ`, `α`) — alone or in a simple expression
- **isotopes alone** (`14C`) and **plain fractions** (`1/2`) — context-dependent
- **ordinals** in `<sup>` (`1st`, `2nd`)
- **temperature degrees**
- single-element molecules (`O2`) or charge-free pairs (`NaCl`)

## References

- MathJax basics: https://math.meta.stackexchange.com/questions/5020/mathjax-basic-tutorial-and-quick-reference
- Degree/ASCII codes: https://websitebuilders.com/tools/html-codes/ascii/
