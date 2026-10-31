# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

John Chodera's curriculum vitae as a single LaTeX document. `CV.tex` is the only source file; `CV.pdf` is the compiled output and is committed alongside source changes (commits typically include `CV.tex`, the rebuilt `CV.pdf`, and any new thumbnails).

## Build

```sh
latexmk -pdf CV.tex     # or: pdflatex CV.tex (run twice for hyperref/marginpars)
```

Uses pdflatex with the `lato` font package. No bibliography tool — all references are written inline. Run `latexmk -c` afterward to remove auxiliary files (they are not tracked). Every file `CV.tex` references must be committed, or a fresh checkout won't build.

## Structure of CV.tex

- **Preamble (top ~230 lines)** defines custom macros. Many alternate layouts are kept as commented-out variants; leave them in place.
- **`\jdc`** — renders the highlighted "Chodera JD" in author lists. Always use it instead of typing the name.
- **`\newarticle{thumb}{authors}{title}{journal ref}{link label}{url}{blurb}`** — the entry format for every publication/preprint. `thumb` is a filename in `thumbnails/` (extension optional; graphicx resolves it). Link label is usually `DOI`, `bioRxiv`, `chemRxiv`, etc.; preprints use `\emph{Preprint}` as the journal ref.
- **`\collaboration{thumb}{name}{dates}{url}{blurb}`** — Major Research Collaborations entries.
- **`\talk{date}{location}Title \\ {\small Venue}\vspace{0.5ex}`** — talk entries (date/location go in the margin).
- Author-list conventions (stated in the Preprints header): `\underline{Name}` = Chodera lab trainee; `$\ddag$` = co-corresponding; `$^*$` = co-first; `$\dag$` = co-second. Use LaTeX accent escapes (`\"{o}`, `\'{e}`) for non-ASCII names.

### Publication sections

- `Preprints` and `All Published and In Press Publications` list newest first; new entries are added at the top of the relevant section, preceded by a date comment like `%%% 2026-01-09`.
- When a preprint is published, move its `\newarticle` from Preprints into the published section and update the journal ref/link.
- The `All Publications` header block contains hand-maintained citation stats (h-index, citation count, date) and a citations-per-year figure (`thumbnails/citations-YYYY-MM-DD.pdf`, generated from `images/citations-per-year.key`); update both the numbers and dates together.

### Other sections

Funding (Active / Pending / Completed), Personnel (current members / past trainees), Recent Invited Talks, service, etc. follow the plain-text patterns already present in each section — copy a neighboring entry.

## Thumbnails

`thumbnails/` holds one image per paper/collaboration (often both `.pdf` and `.jpg` versions). Add a new thumbnail file for each new `\newarticle` entry and reference it by basename.
