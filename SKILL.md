---
name: exam-cheatsheet-latex
description: Convert user-provided Word, PDF, or slide/image materials into a dense, editable, black-and-white A4 exam cheat sheet in Overleaf-ready LaTeX and a print-ready PDF. Use for exam notes with pseudocode, proofs, math, or multilingual text when source fidelity and space efficiency matter.
---

# Exam Cheat Sheet — Source-Faithful LaTeX

## Purpose

Convert the **latest source document(s) explicitly selected by the user** into a compact, editable LaTeX cheat sheet for A4 printing. The default target is **two A4 pages (double-sided), four columns per page**, with readable 6 pt text. Preserve every piece of source content, including text embedded in screenshots, pseudocode, mathematical expressions, proofs, labels, and section titles.

This is a **formatting and faithful transcription** task, not a rewriting, summarization, fact-checking, or tutoring task.

## Source fidelity — non-negotiable

1. Read **all pages** of the selected file(s), including embedded images. Do not rely on text extraction alone: inspect images for text, math, pseudocode, and labels.
2. Preserve the source's **original wording, language, ordering, notation, algorithm steps, conclusions, and mathematical claims**. Do not add outside knowledge, explanations, corrected proofs, missing steps, or new examples.
3. Convert every informative image to **editable text/LaTeX**. Reproduce formulas in real LaTeX math mode and code/algorithm screenshots as editable pseudocode. Preserve labels and captions where they carry information. Do not paste screenshots into the sheet.
4. If an image contains a purely visual diagram, preserve its legible textual content and relationships in text **only where faithfully expressible**; never invent diagram details. If material cannot be represented without loss, report the limitation separately rather than claiming complete transcription.
5. Keep repetitions that exist in the source unless the user explicitly authorizes deduplication. Do not silently repair source mistakes; if a passage is ambiguous, transcribe it as-is when possible and flag the ambiguity outside the artifact.
6. Default to the **latest uploaded version** for replacement workflows. Do not merge earlier versions or previously generated content unless the user expressly asks.
7. Keep the cheat sheet free of additional content: **no new title page, index, study tips, citations, explanations, or decorative filler** beyond what is in the source.

## Default page and type settings

| Setting | Default |
|---|---|
| Paper | A4, portrait, designed for double-sided printing |
| Target length | 2 pages, **best effort**; never drop content to hit the target |
| Columns | **3**, automatically flowing |
| Margins | **4 mm** on all sides, subject to printer's printable area |
| Column separation | about **2.5 mm**; adjustable for fit |
| Body font | **TeX Gyre Termes**, 6 pt |
| Body baseline | **6.0 pt** |
| Chinese text | CJK serif font available in Overleaf (e.g. FandolSong-Regular) |
| Color | **Black text on white**; no color panels or embedded images |
| Paragraph spacing | 0 pt; no unnecessary indentation |
| Lists | Minimal left margin, `topsep=0pt`, `itemsep=0pt`, `parsep=0pt` |
| Display-math vertical skips | All set to **0 pt** |
| `\jot` | **0 pt** |
| Compiler | **XeLaTeX** (supports English, Chinese, and mathematics) |

Do not automatically lower the body font below 6 pt simply to force two pages. If the content does not fit on two pages, preserve the full content and report the resulting page count. Any change to defaults should be explicitly requested or justified by legibility/printing concerns.

## Formula layout: favor inline math

Use the **fewest possible forced line breaks**, without clipping text or scaling formula glyphs to unreadable sizes.

- Convert short, ordinary display formulas to inline `\(...\)` (or `$...$`) when they fit naturally in a paragraph.
- Keep connective text and the formula **on the same line where feasible**. For example, instead of a separate line for `Thus:` and a displayed equation, use `Thus: $\boxed{T(n)=n\log_2 n}$ for ...`.
- Combine related short identities and complexity claims using commas, semicolons, or `\quad`, without deleting labels or explanatory text from the source.
- Retain **standalone display math** for multi-line derivations, long recurrences, `cases`, aligned inequalities, matrices, and formulas that would overflow a column.
- Keep `\boxed{...}` when present in the source, but avoid a standalone displayed box when the boxed formula fits inline. Do not introduce boxes unnecessarily.
- Avoid `\[...\]` around simple single-line formulas. Avoid an isolated display immediately after a one-word prefix (`Thus:`, `Therefore:`, `Complexity:`, `subject to:`) when inline placement fits.
- Avoid `\resizebox` as a default fix; first prefer semantic line breaking or a legitimate compact equivalent without losing mathematical structure. Never knowingly create overfull columns.
- Set the following lengths to zero, and verify they remain in force at document start:

```latex
\setlength{\abovedisplayskip}{0pt}
\setlength{\belowdisplayskip}{0pt}
\setlength{\abovedisplayshortskip}{0pt}
\setlength{\belowdisplayshortskip}{0pt}
\setlength{\jot}{0pt}
```

## Text, proof, and pseudocode layout

- Preserve proof steps, algorithm ordering, complexity statements, and all source wording.
- Use compact headings (bold, modest spacing), not large section titles.
- Avoid excessive vertical gaps before and after headings, formulas, bullets, paragraphs, and algorithms.
- Format pseudocode as **real text**, not raster graphics. Use a compact monospaced style or equivalent formatting; preserve indentation and control-flow structure, but allow safe line wrapping within narrow columns.
- Render mathematical tokens within pseudocode as LaTeX math when practical; choose clarity over decorative syntax highlighting.
- No colored backgrounds, screenshots, banners, logos, or illustrative graphics in the final cheat sheet.
- Mixed Chinese/English must render without missing glyphs; use XeLaTeX and a CJK font available in the target environment.

## Workflow

1. **Determine scope:** use the latest uploaded file by default, or the specific document(s) the user names. Preserve original contents; do not merge older files by assumption.
2. **Inspect source:** extract DOCX paragraphs/tables and embedded media; inspect all pages, all meaningful image text, equations, and pseudocode. PDF pages may require image inspection when text parsing misses content.
3. **Transcribe faithfully:** produce editable LaTeX in source order; retain every substantive phrase, math symbol, algorithm, and proof. Use correct math markup, not literal `\(` and `\)` printed on the page.
4. **Apply compact layout:** start from `assets/template.tex`. Put short formulas inline, preserve complex formulas as display math, and minimize whitespace.
5. **Compile** with XeLaTeX. Fix missing glyphs, math-mode errors, overflow, broken pseudocode, strange wrapping, and unintended blank space. Ensure it is actually print-ready, not merely syntactically valid.
6. **Inspect the output visually** on every page, including columns, equation widths, page endings, margins, and CJK text. Confirm no meaningful content is omitted or duplicated.
7. **Deliver** an editable `.tex` file and a compiled `.pdf` file. Clearly state actual page count and whether the two-page target was achieved; disclose any transcription uncertainty separately.

## Priority order on conflict

1. **Source completeness and fidelity** (no additions, omissions, silent fixes)
2. **Legibility and correct rendering** (no overlapping glyphs/overflow)
3. **6 pt body font and 6 pt baseline**, unless user specifies otherwise
4. **Two A4 sides**, four-column dense layout, minimal whitespace

Never claim that all content was preserved, an output compiled successfully, or a two-page limit was met unless it was actually checked.

## Output filenames

Use straightforward filenames such as `Exam_Cheat_Sheet.tex` and `Exam_Cheat_Sheet.pdf`. For user-requested versions, append a meaningful suffix (e.g. `_6pt`, `_Inline`).
