# NIU Dissertation in LaTeX (via GitHub Codespaces)

This repository provides NIU graduate students with a free, GitHub-based alternative to Overleaf for writing their dissertation in LaTeX. It combines <a href="https://github.com/sanjib-sen/weblatex" target="_blank" rel="noreferrer noopener">Sanjib Sen's WebLaTex project</a> — which sets up a full LaTeX editing environment inside a GitHub Codespace using VS Code — with the `niuthesis` document class created by <a href="https://www.niu.edu/rwinkler/tex/niuthesis/index.htm" target="_blank" rel="noreferrer noopener">Roland Winkler</a>, which formats your document to meet NIU Graduate School requirements.

If you've been using Overleaf, this setup gives you the same browser-based LaTeX editing experience, plus the full power of Git version control, GitHub Copilot, and Grammarly for free.

## Why Use This Instead of Overleaf?

| Feature | Overleaf (Free) | Overleaf (Paid) | This Repo |
|---|---|---|---|
| Browser-based editing | ✅ | ✅ | ✅ |
| Git integration | ❌ | ✅ ($40/mo) | ✅ |
| Collaborate with advisor | 1 person | ✅ | ✅ (Live Share) |
| GitHub Copilot | ❌ | ❌ | ✅ |
| Cost | Free | $40/mo | Free |

## What's in This Repo?

```
niuthesis/
├── .devcontainer/        # WebLaTeX Codespace configuration
├── diss/                 # 📝 Your dissertation goes here
│   ├── diss.tex          # Main file — start here
│   ├── niuthesis.cls     # NIU thesis document class (Winkler, 2015)
│   ├── refs.bib          # Bibliography file (BibTeX format)
│   └── Chapter1/
│       └── ch1.tex       # Starter Chapter 1 with instructions
├── example/              # Complete example dissertation for reference
│   ├── mythesis.tex      # Main file (shows document structure)
│   ├── niuthesis.cls
│   ├── Chapter1/         # ch1.tex, app1.tex
│   ├── Chapter2/         # ch2.tex, app2.tex
│   └── refs.tex          # Manual bibliography (for reference only)
├── nondissdemo.tex       # Simple intro LaTeX demo
└── WebLaTeXREADME.md     # Full WebLaTeX documentation
```

The `example/` folder contains a fully working fake dissertation demonstrating tables, figures, equations, sideways tables/figures, appendices, and bibliography. **Look here when you get stuck** — it covers most of what you'll need. Note that the example uses a manual bibliography; your starter files in `diss/` use BibTeX instead, which is easier to manage for a full dissertation.

## Getting Started

### 1. Set Up Your Codespace

1. Click the green **"Use this template"** button at the top of this page and create your own repository.
2. In your new repo, click **`<> Code`** → **`Codespaces`** → **`Create Codespace on Main`**.
3. Wait about 2 minutes on the first launch while the LaTeX environment installs. After that, it opens in seconds.

### 2. Fill In Your Information

Open `diss/diss.tex`. At the top of the document, fill in your title, name, degree information, and advisor:

```latex
\title{Your Dissertation Title Here}
\author{Your Name}
\major{Your Major/Program}
\degree{Dissertation}{Ph.D.}{Doctor of Philosophy}
\degreedate{May}{Year}
\department{Department of XXXX}
\director{Your Advisor's Name}
```

Then fill in your abstract, acknowledgments, and (optionally) dedication in the environments provided.

### 3. Write Your Chapters

Each chapter lives in its own `.tex` file. The repo includes a starter `Chapter1/ch1.tex` with instructions. To add more chapters:

1. Create a new folder (e.g., `Chapter2/`) and add a file `ch2.tex` inside it.
2. Add the chapter to both the `\def\files{...}` line and the `\include{...}` line in `diss.tex`:

```latex
\def\files{Chapter1/ch1,Chapter2/ch2,refs}
...
\include{Chapter1/ch1}
\include{Chapter2/ch2}
```

You do **not** need `\begin{document}` or `\end{document}` in chapter files — just start writing content directly.

### 4. Manage Your References

Add bibliography entries to `diss/refs.bib` in BibTeX format. For example:

```bibtex
@book{booth2008craft,
  author    = {Booth, Wayne C. and Colomb, Gregory G. and Williams, Joseph M.},
  title     = {The Craft of Research},
  edition   = {3rd},
  publisher = {University of Chicago Press},
  address   = {Chicago},
  year      = {2008},
}
```

Then cite sources in your chapters using `\cite{booth2008craft}`, `\citep{booth2008craft}` (parenthetical), or `\citet{booth2008craft}` (in-text narrative). Check with your advisor or committee about which citation style your field uses — change `\bibliographystyle{chicago}` in `diss.tex` accordingly.

### 5. Add Appendices

Appendices go after `\appendix` in `diss.tex`. Uncomment and add `\include{}` lines as needed. You can organize them by chapter (e.g., `Chapter1/app1.tex`) or keep them all in the main `diss/` folder — just make sure the path in `\include{}` matches where the file actually lives.

### 6. Compile Your PDF

- Press **`Ctrl+S`** to save and compile. Your PDF will appear in the `PDF/` folder.
- Click the PDF file in the file explorer to preview it. **It may take 20–30 seconds the very first time.**
- If you see "Error showing PDF," press `Ctrl+R` to reload.
- Check the **Terminal → Output → Latex Compiler** panel for error messages if something doesn't compile.

### 7. Save Your Work

Commit and push your changes to GitHub regularly — this is your version control. You can roll back to any previous state of your document at any time, which is especially useful when your advisor asks you to restore a section you deleted three months ago.

## Tip: Working on One Chapter at a Time

Compiling the full dissertation every time gets slow. To work on just one chapter, comment out the full `\def\files` line and uncomment the single-chapter version:

```latex
%%% use this to compile all chapters
% \def\files{Chapter1/ch1,Chapter2/ch2,refs}

%%% use this to work with only one chapter
\def\files{Chapter2/ch2}
```

Do the same with the `\include{}` lines below. Just remember to switch back before your final compile.

## NIU Dissertation Requirements

The `niuthesis` class handles most formatting automatically (margins, spacing, title page, table of contents, etc.), but you should familiarize yourself with the official NIU Graduate School guidelines:

- <a href="https://www.niu.edu/grad/thesis/index.shtml" target="_blank" rel="noreferrer noopener">NIU Graduate School: Thesis & Dissertation</a>
- <a href="https://www.niu.edu/grad/_pdf/thesis/etd-guidelines-thesis.pdf" target="_blank" rel="noreferrer noopener">NIU ETD Guidelines (PDF)</a>
- <a href="https://www.niu.edu/grad/thesis/templates-examples.shtml" target="_blank" rel="noreferrer noopener">NIU Templates & Examples</a>
- <a href="https://www.niu.edu/grad/thesis/documentation-styles.shtml" target="_blank" rel="noreferrer noopener">NIU Documentation Styles</a>
- <a href="https://www.niu.edu/rwinkler/tex/niuthesis/index.htm" target="_blank" rel="noreferrer noopener">Roland Winkler's niuthesis documentation</a>

## Learning LaTeX

New to LaTeX? These resources will get you up to speed:

- <a href="https://www.overleaf.com/learn/latex/How_to_Write_a_Thesis_in_LaTeX_(Part_1)%3A_Basic_Structure" target="_blank" rel="noreferrer noopener">How to Write a Thesis in LaTeX — Overleaf</a>
- <a href="https://www.overleaf.com/learn/latex/Free_online_introduction_to_LaTeX_(part_1)" target="_blank" rel="noreferrer noopener">Free Online Introduction to LaTeX — Overleaf</a>
- <a href="https://groups.tecnico.ulisboa.pt/~neiist.daemon/docs/latex_tutorial.pdf" target="_blank" rel="noreferrer noopener">LaTeX Tutorial (PDF) — Instituto Superior Técnico</a>
- <a href="https://web.uri.edu/engineering/thesisguide/" target="_blank" rel="noreferrer noopener">LaTeX Thesis Guide — University of Rhode Island</a>

## Credits

- **WebLaTeX** by <a href="https://github.com/sanjib-sen/weblatex" target="_blank" rel="noreferrer noopener">Sanjib Kumar Sen</a> — VS Code + GitHub Codespaces LaTeX environment
- **niuthesis document class** by <a href="https://www.niu.edu/rwinkler/" target="_blank" rel="noreferrer noopener">Roland Winkler</a>, Northern Illinois University (GNU GPL v3)
- **Additional extensions**: [LaTeX Workshop](https://github.com/James-Yu/LaTeX-Workshop), [Grammarly](https://github.com/znck/grammarly), [GitHub Copilot](https://github.com/features/copilot), [Live Share](https://visualstudio.microsoft.com/services/live-share/)
