# LaTeX and Beamer

LaTeX is built on top of TeX and is mainly used for technical reports, papers and anything heavy on formulas. Instead of dragging formatting around in Word, you write plain text commands in a .tex file and compile it to PDF.

## Compiling
- Desktop tools: MiKTeX + TeXstudio on Windows, TeX Live on Linux
- Browser editor: Overleaf
- Quick compile: pdflatex report.tex
- Order when using bibliography or index:
  1. latex report
  2. bibtex report (or makeindex report)
  3. pdflatex report
  4. pdflatex report

Running pdflatex twice at the end fixes page numbers and citation numbering.

## Document Layout
A .tex file starts with the preamble (class + packages) followed by the document environment:

```
\documentclass[12pt, a4paper]{article}
\usepackage{amsmath, graphicx, xcolor}

\begin{document}
  \title{Technical Writing Report}
  \author{Arnav Goel}
  \date{\today}
  \maketitle

  \begin{abstract}
    Summary of the report.
  \end{abstract}

  \section{Overview}
  \subsection{Method}
  \section*{Note}
\end{document}
```

- Document classes: article, report, book, letter, beamer, exam.
- report and book allow \chapter{}. book also uses \frontmatter, \mainmatter and \backmatter.
- Mandatory values go inside {} and optional settings go inside [].

## Text, Margins and Headers
- % starts a comment line.
- Blank line creates a new paragraph; \\ forces a line break. \newpage breaks the page, while \clearpage breaks the page and flushes queued floats first.
- Escape special characters with backslash: \$, \&, \%, \#, \_, \{, \}.
- Font sizes: \tiny, \scriptsize, \footnotesize, \small, \normalsize, \large, \Large, \LARGE, \huge, \Huge.
- Alignment: flushleft, center, flushright.
- Page style: \pagestyle{plain}, headings, empty.
- Margins with geometry: \geometry{left=2.5cm, right=2.5cm, top=2.5cm, bottom=2.5cm}.
- Headers/footers with fancyhdr: \pagestyle{fancy}, \fancyhf{}, \fancyhead[L/C/R]{...}, \fancyfoot[C]{\thepage}.
- sectsty changes heading style (\sectionfont{...}), and fontspec loads system fonts under XeLaTeX/LuaLaTeX.

## Lists and Boxes
- itemize = bullet list, enumerate = numbered list, description = labeled items (\item[Key] explanation). enumitem lets you tweak spacing with \setlist.
- trivlist is an unstyled list mostly used when building custom environments via \newenvironment.
- Box commands:
  - \mbox{...} prevents line breaks inside text
  - \parbox{width}{text} makes a fixed-width text block
  - \framebox[w][l/c/r]{text} puts a frame around text
  - \makebox, \raisebox{1ex}{text}, \rule{w}{h}
  - \newsavebox, \savebox and \usebox save reusable boxes

## Equations and Matrices (amsmath, amssymb)
- Inline math: $ ... $ or \( ... \)
- Display math: \[ ... \] or \begin{equation} ... \end{equation} (use equation* to skip numbers)
- Aligned / multi-line math: align* (aligns at &), multline*, gather*
- Common commands: x^2, a_i, \frac{a}{b}, \sqrt[3]{x}, \sum_{i=1}^{n}, \prod, \int_0^\infty, \binom{n}{k}, \alpha, \beta, \leq, \neq, \cup, \cap
- Piecewise functions: array environment inside \left\{ ... \right.
- Matrices: matrix, pmatrix (), bmatrix [], Bmatrix {}, vmatrix ||, Vmatrix ||||, smallmatrix (inline). Columns split with & and rows with \\ (like \\[6pt] for extra row gap).

## Tables
```
\begin{table}[h!]
  \centering
  \begin{tabular}{|l|c|r|}
    \hline
    \multicolumn{3}{|c|}{Summary} \\ \hline
    P & Q & R \\ \hline
  \end{tabular}
  \caption{Sample Data}
  \label{tab:data}
\end{table}
```
- Specifiers: l, c, r, p{1.5cm}.
- Merge cells using \multicolumn{cols}{align}{text} and \multirow{rows}{width}{text}.
- Float placement: h, t, b, p, !, H.
- Styling: \arrayrulewidth, \tabcolsep, \arraystretch, and colortbl (\rowcolor, \columncolor, \cellcolor).

## Colors, Figures, Graphics and References
- xcolor: \textcolor{red}{text}, \definecolor{myblue}{RGB}{10,60,200}, \colorbox{yellow}{text}, \fcolorbox, \pagecolor{yellow!10}.
- graphicx: \includegraphics[width=0.5\textwidth, scale=0.5, angle=30]{img}. Use figure environment for \caption and \label, and minipage for side-by-side images.
- Cross-references: \label{fig:1} with \ref{fig:1} or \pageref{fig:1}.
- picture environment uses \unitlength and coordinates: \put(x,y){\vector(dx,dy){len}}, \line(dx,dy){len}, \circle{d}, \circle*{d}, \oval(w,h), \dashbox, \qbezier(p1)(p2)(p3), \multiput.
- BibTeX: store entries (@article, @BOOK) in .bib, cite with \cite{key}, put \bibliographystyle{plain} and \bibliography{refs}.
- makeidx: \makeindex in preamble, \index{term}, \printindex at end.
- Debugging: read the .log file line numbers (Undefined control sequence, Missing \begin{document}, Lonely \item, column mismatch in tabular).

## Beamer Presentations
Beamer makes PDF slides in LaTeX using frame blocks instead of sections/pages:

```
\documentclass{beamer}

\title{TW Slides}
\author{Arnav Goel}
\date{\today}

\begin{document}

\begin{frame}
  \titlepage
\end{frame}

\begin{frame}{Agenda}
  \begin{itemize}
    \item Part 1
    \item Part 2
  \end{itemize}
\end{frame}

\end{document}
```

- Abstract in Beamer: use \begin{frame}{Abstract} ... \end{frame} (there is no \begin{abstract}).
- Overlays: \pause or <1-> reveals bullets step by step.
- Code slides: add [fragile] to any frame with verbatim or code blocks, otherwise it fails to compile:

```
\begin{frame}[fragile]{Snippet}
\begin{verbatim}
print("Beamer slide")
\end{verbatim}
\end{frame}
```

- Math, colors, tables, minipage and includegraphics work inside Beamer frames too.
