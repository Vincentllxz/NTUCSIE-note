# NTUCSIE-note

My LaTeX lecture notes for courses at **National Taiwan University, CSIE**.

Each course lives in its own folder and compiles into a single PDF. Notes are
typeset with **XeLaTeX** (CJK support via `xeCJK`), bibliographies via
`biblatex`/`biber`, code listings via `minted`, and figures via the `svg`
package.

## Repository layout

A typical course folder looks like this:

```
<Course>/
├── <Course>.tex      # main document — compile this one
├── header.tex        # preamble: packages, fonts, page geometry
├── Math.tex          # shared math macros / operators
├── ListStyle.tex     # list and enumerate styling
├── appendix.tex      # appendix content
├── reference.bib     # bibliography
├── Lectures/         # one file per lecture (lec_1.tex, lec_2.tex, ...)
└── Figures/          # figures (svg / pdf / png / jpg)
```

`cover/` holds the shared title-page template.

## Building

The notes use XeLaTeX with `-shell-escape` (required by `minted`). Figures use
the `svg` package, which needs **Inkscape** on your `PATH` to convert `.svg`
to PDF at build time; `minted` needs **Pygments** (`pip install Pygments`).

Compile a course (e.g. ADA) from inside its folder:

```bash
cd ADA
latexmk -xelatex -shell-escape ADA.tex
```

Or run the steps manually:

```bash
cd ADA
xelatex -shell-escape ADA.tex
biber ADA
xelatex -shell-escape ADA.tex
xelatex -shell-escape ADA.tex
```

## Notes

- Source files and the compiled note PDFs are tracked, so you can read a course
  without building it. LaTeX build artifacts (`.aux`, `.log`, `.synctex.gz`,
  `_minted/`, etc.) are git-ignored — see `.gitignore`.
- These are personal study notes and may contain mistakes. Use at your own
  risk, and feel free to open an issue if you spot an error.
