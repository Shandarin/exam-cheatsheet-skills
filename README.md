# Exam Cheat Sheet LaTeX Skill

An [Agent Skill](https://agentskills.io/) for converting user-provided Word, PDF, and slide/image material into a **dense, editable, source-faithful A4 exam cheat sheet** in LaTeX.

**Key principle:** Preserve the source content. This is a transcription and layout skill, **not** a summarizer or a tutor.

## Features

- Transcribe embedded screenshot text, math, and pseudocode into editable LaTeX.
- Preserve original wording, content order, proofs, and notation; flag material that cannot be faithfully converted.
- A4 layout, four columns, 4 mm margins, 6 pt font, 6 pt baseline by default.
- Black-and-white, print-focused formatting.
- Inline short equations to reduce whitespace; retain display math for complex recurrences and multi-line derivations.
- XeLaTeX and CJK support for mixed Chinese/English material.
- Target two A4 pages when possible **without discarding content**.
- Deliver both `.tex` and `.pdf` after compilation and visual inspection.

## Repository structure

```text
exam-cheatsheet-latex/
├── SKILL.md
├── README.md
├── LICENSE
├── .gitignore
└── assets/
    └── template.tex
```

## Installation

Copy this repository (including `SKILL.md` and the `assets` directory) into a skills directory supported by your AI agent. The exact skills path and activation method depend on the agent or editor.

Read [`SKILL.md`](SKILL.md) for the full instructions. The base Overleaf template is in [`assets/template.tex`](assets/template.tex).

## Example request

> Convert this Word document to a two-sided A4 LaTeX exam cheat sheet. Preserve all source content, including embedded pseudocode and formulas. Use the skill's default dense black-and-white layout; return a `.tex` file and a compiled `.pdf`.

## Requirements

- A model/toolchain able to extract and inspect the supplied documents, including embedded images.
- XeLaTeX with the fonts/packages required by `assets/template.tex` to compile the generated output.
- PDF rendering/inspection to confirm no overflows or missing content.

This repository provides **instructions and a template**, not an end-to-end executable document converter. Results depend on the host agent's document-reading, compilation, and image-understanding capabilities.

## Source material and rights

Only process files you have permission to use. Do not commit private course documents, protected exams, uploaded source files, or third-party screenshots into this public repository without authorization. No user material is included here.

## License

MIT — see [`LICENSE`](LICENSE). **Before publishing, replace the placeholder copyright holder in that file with your name or organization.**
