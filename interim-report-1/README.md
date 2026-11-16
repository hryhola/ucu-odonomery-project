# Interim report 1

Source: `LA-report-template-2026.tex` (pdfLaTeX). Limit: **2 pages**, project card included.

## Build & preview

- **VS Code (live preview):** install the recommended extension *LaTeX Workshop*, open the folder, and save the `.tex`. It rebuilds and shows the PDF in a tab. `Cmd+Option+V` opens the preview, and `Cmd+click` in the PDF jumps to the source.
- **Terminal:** `make pdf` builds once. `make watch` rebuilds on every save. `make open` opens the PDF. `make clean` removes the build output.

Build artifacts go to `build/`. The final PDF is copied next to the source.

## Sequence of things to do

1. Add `UCU-Apps.png` (the logo) to this folder.
2. Fill in the **FILL IN** block: stage (interim 1), title, authors, project card and links.
3. Replace each grey guidance box with your own text.
4. Do **not** change the font size, the paper size or the margins.
5. Build and check the page count at the end of `build/*.log`. It must be 2 or fewer.
6. Before submitting:
   - set `\showguidefalse`
   - remove the `\todo{}` notes, or add `disable` to the `todonotes` options
   - check the log for warnings about undefined references
7. Submit the PDF.

This one `.tex` file grows into interim report 2 and then the final report, so keep working in it.
