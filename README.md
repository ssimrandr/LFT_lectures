# Lecture Notes

This repository contains LaTeX lecture notes organized by week. It is intentionally minimal and focused on source `.tex` files and figures. The `.gitignore` is already set up to ignore common LaTeX build files (aux, log, pdf, etc.).

Repository layout

```
lecture-notes/
├── README.md              ← this file: describes what this repo is
├── .gitignore             ← already set up to ignore LaTeX build files
├── week01/
│   └── lecture01.tex
├── week02/
│   └── lecture02.tex
└── figures/
    └── diagram1.png
```

What this repo is for

- Store source LaTeX for lecture slides/notes, one lecture per `.tex` file.
- Keep figures in a single `figures/` directory for reuse across weeks.
- Track only source files; build artifacts are ignored.

Quick usage / how to build

Each lecture is a standalone `.tex` file in its `weekNN/` folder. You can compile a lecture from its folder. Below are a few recommended workflows.

1) Recommended (best option): use `latexmk` for reliable builds and automatic cleanup:

```bash
# from repository root, compile week01 lecture
cd week01
latexmk -pdf lecture01.tex
# clean up auxiliary files created by latexmk:
latexmk -c
```

On macOS you can install `latexmk` by installing MacTeX or BasicTeX (or via package managers if available).

2) Simpler (single run with xelatex or pdflatex):

```bash
# xelatex (good for system fonts and unicode):
cd week01
xelatex -interaction=nonstopmode lecture01.tex

# or pdflatex:
pdflatex -interaction=nonstopmode lecture01.tex
```

Notes

- If your lectures include bibliographies or cross-references, prefer `latexmk` (it runs bibtex/biber and multiple passes automatically).
- The `.gitignore` already excludes typical build outputs: `.aux`, `.log`, `.out`, `.pdf`, and intermediate files. Commit only `.tex`, figures, and small config files.

Figures

- Put figures (PDF/PNG/SVG) in `figures/` and reference them with relative paths, e.g. `\includegraphics{../figures/diagram1.png}` from within a `weekNN/` folder.
- Keep figure sources (e.g., .svg) if you need to regenerate or edit diagrams.

Adding a new lecture

- Create a new folder `week03/` and add `lecture03.tex`.
- Follow the same structure and include graphics from `../figures/` or add week-specific figures inside the week folder if preferred.
- Add content, test local compilation, then commit the `.tex` source (not the built `.pdf`).

Contributing

- Open a PR with changes to a lecture or figures.
- Keep each lecture focused and small; avoid committing large binary files unless necessary.

License & contact

- This repository doesn't include a license by default. Add a `LICENSE` file if you plan to share or publish the notes.
- For questions or help with compilation, contact the repo owner or maintainer.

Happy writing!
