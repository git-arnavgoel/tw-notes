# Doxygen and Google Docs

## Doxygen
Doxygen builds reference documentation (HTML, LaTeX/PDF, RTF, XML) automatically by reading special comments inside source code (C, C++, Python, Java).

Workflow:
1. Check install: doxygen --version
2. Add doc comments in code.
3. Generate config: doxygen -g Doxyfile
4. Configure Doxyfile if needed: GENERATE_HTML = YES, GENERATE_LATEX = YES, HAVE_DOT = YES (Graphviz call graphs and inheritance diagrams).
5. Run: doxygen Doxyfile
6. Open html/index.html in browser.

C++ comment example:
```
/**
 * \brief Multiplies two integers.
 * \param x First number
 * \param y Second number
 * \return Product of x and y
 */
int multiply(int x, int y);
```
Classes use \class ClassName and \brief.

Python docstring example:
```
def cube(n):
    """
    Compute cube of n.
    :param n: Input integer
    :type n: int
    :return: Cubed integer
    :rtype: int
    """
    return n * n * n
```

Main tags: \brief, \param, \return, \author, \version, \see, \note.
Keep Doxyfile tracked in Git, explain behavior rather than repeating parameter names, and host generated html docs on GitHub Pages if needed.

## Google Docs
Google Docs is a cloud word processor meant for team reports, proposals, meeting notes and collaborative drafts.

Features covered in class:
- Real-time co-editing with live cursors.
- Sharing roles: Viewer, Commenter, Editor.
- Comments and Suggesting mode: attach/assign/resolve comments on text, or switch to Suggesting so edits appear as proposals for approval.
- Version History: auto-saves changes; File -> Version history lets you view history, name versions and restore older copies.
- Heading styles: use Title, Subtitle, Heading 1, Heading 2 instead of manual bolding so an automatic Table of Contents works.
- Inserts and citations: Insert -> Table / Image / Drawing / Equation (or draw.io / Lucidchart add-ons); Tools -> Citations for MLA, APA, Chicago bibliographies; download as pdf, docx, odt, html, txt.

Doxygen vs Google Docs: Doxygen documents source code/APIs alongside Git, while Google Docs handles team planning docs, proposals and live collaborative writing.
