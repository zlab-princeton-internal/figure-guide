[中文版](README_CN.md)

# Figure & Table Guide

## General Principle

- In a good paper, a reader should be able to understand your core claims and conclusions just by scanning the key figures and tables — at most glancing at the captions, ideally without reading any body text. If readers must read the text to understand your most important figures, the figures are not clear enough.
- Important figures and tables should have detailed captions. Do not write a one-line or half-line caption for your core results.

## Font (Most Common Issue — Please Get This Right)

- **Please use Arial (or Helvetica) for text in diagrams and flowcharts.** Do not use serif fonts.
- **Text size in figures should be close to the caption size — it can be slightly larger, but must never be much smaller.** The most common mistake is text that is way too small. Always check in the compiled PDF at 100% zoom.

These two points are the most frequently repeated feedback. Get these right and most problems go away.

- **Do not bold text in diagrams/flowcharts.** Bolding does not improve readability — it just looks worse. At most, bold a few specific words for emphasis. Never bold an entire category of text.

## Workflow

- **Sync Overleaf with Dropbox** so that figures you generate locally are automatically synced to Overleaf — no need to manually drag and upload each time. This saves a lot of time. Setup: [Overleaf-Dropbox sync](https://www.overleaf.com/learn/how-to/Dropbox_Synchronization).

## Format

- **Always export figures as PDF** (vector graphics). Never use PNG/JPG for plots. PDF stays sharp when zooming in and text remains selectable.
- **Crop all white space** around figures. In matplotlib, use `plt.savefig(..., bbox_inches='tight')`.

## Visual Style

- **Add thin black borders to boxes/rectangles** in diagrams. This makes them look more polished.
- **Use thin, pure black, borderless arrows** in diagrams (the default thin arrow in PowerPoint/Keynote works well).
- **Text and borders should mostly be pure black** (high contrast). Avoid gray — it looks like a webpage, not an academic paper.
- **Text inside boxes should fit the box size.** Do not leave large gaps on all four sides — at least top/bottom or left/right should be close to the box edges.
- Consider a **dark background + white text** style for boxes.

> **Fig. 1** — Thin arrows + thin black borders + dark bg with white text + text fitting the box. From [DyT](https://arxiv.org/abs/2503.10622).
>
> <img src="examples/dyt_diagram.png" width="500">

- **Replace unnecessary dividing lines with colored background blocks** (see Fig. 5).
- **Pay attention to the spacing between figure and caption, and between caption and body text.** This spacing is often too large or too small — adjust it manually. Once you are aware of this, you will get it right.
- **Figures should not be too sparse or too crowded internally.** Keep arrows short — they should roughly fill the gap between boxes. Avoid situations where two boxes are far apart with only a tiny arrow in between.
- **Remove all vertical lines in tables.**

## Diagrams & Teasers

- **Express your core idea in one simple figure.** Do not draw overly complex pipeline diagrams (multiple rows, multiple columns, every component annotated with colors). Simpler is better.
- Use **side-by-side comparison** (old method vs. yours) to make the difference immediately clear.

> **Fig. 2** — One simple figure captures the entire core mechanism. From [MoCo](https://arxiv.org/abs/1911.05722).
>
> <img src="examples/moco_fig1.png" width="300">

> **Fig. 3** — Three methods side by side, consistent structure, differences obvious at a glance. From [MoCo](https://arxiv.org/abs/1911.05722).
>
> <img src="examples/moco_fig2.png" width="700">

> **Fig. 4** — Left-right comparison with concrete numbers, instantly understandable. From [Wanda](https://arxiv.org/abs/2306.11695).
>
> <img src="examples/wanda_fig1.png" width="700">

## Content

- If your work involves **vision generation**, you must show generation samples — not just numerical tables and plots.
- **Show concrete examples** (dataset samples, environment screenshots, model outputs, etc.) so readers can see what your data and results actually look like. Especially important for data-centric work.

> **Fig. 5** — Colored background blocks instead of dividing lines for data samples. Color palette reference. From WorldBench (upcoming).
>
> <img src="examples/colorbox_example.png" width="700">

## Pseudocode / Code

- If your method is simple enough, consider including pseudocode or real code (e.g., PyTorch) to describe the core algorithm. This greatly helps clarity.
- Use real code when the method is simple; use pseudocode for more conceptual descriptions.

> **Fig. 6** — A few lines of PyTorch code explain the entire algorithm. From [Wanda](https://arxiv.org/abs/2306.11695).
>
> <img src="examples/wanda_algo.png" width="350">

## Layout

- **Important figures should take the full width.** Do not squeeze a key figure alongside unrelated plots to save space. One row should convey one concept. If you only have one important figure, make a related companion figure to fill the row rather than pairing it with an unrelated ablation.
- Less important figures (ablation, side analysis) can share a row (two per row).
- If you cannot fill a row, use `wrapfigure` to embed the figure alongside text. Do not force it.
- **Figures should be within half a page of where they are first referenced.** Early figures (Figure 1/2) can be placed ahead for framing, but from the experiments section onward, keep figures close to their references.
- **Side-by-side figures: the gap between them should be centered on the page** (or close to it). Do not let y-axis labels/ticks push everything to the right — shrink the figures or leave whitespace on the right to maintain visual symmetry. If there is an overall caption, it should also be centered on the page.
- **Vertically align side-by-side subfigures**: the overall visual center of gravity (including titles and labels) should appear level. Design subfigures with consistent structure (both have titles on top, or neither does). If captions are separate ((a) and (b)), their first lines must align, and the number of caption lines should be similar.
- **Never have two consecutive pages without any figure or table.** Even one page without a figure/table should be rare.

## Variety & Rhythm

- **Use a variety of figure types**: line plots, bar charts, heatmaps, diagrams, etc. Do not use the same type throughout. Table sizes should also vary. But do not force variety for its own sake — keep it natural.
- **Interleave figures and tables** throughout the paper. Do not cluster all figures on one page and all tables on another. The layout should have rhythm and visual appeal.
- See [Cambrian-1](https://arxiv.org/abs/2406.16860) for a good example of figure/table arrangement.

## Plots (matplotlib)

- **Use matplotlib** for plots. Do not use HTML-based tools (Plotly, D3, etc.) for paper figures.
- **Line plots and scatter plots should be slightly wider than tall** — a landscape rectangle. Avoid squares, and especially avoid portrait orientation (taller than wide).
- Consider adding **faint dashed grid lines** as background in line plots for better structure and easier value reading.
- **Bar chart bars must be sharp rectangles.** No rounded corners.
- **Iterate on color choices.** Do not pick colors casually. Refer to DyT and MoCo papers for color schemes, and the colored blocks in Fig. 5 (lighten as needed). (Recommended palettes to be added later.)
- **Heatmap colors are hard to get right.** See Fig. 7 for a reference.

> **Fig. 7** — Heatmap color scheme reference (red-yellow-green). From WorldBench (upcoming).
>
> <img src="examples/heatmap_example.png" width="450">

## References

- All figures and tables must be referenced at least once in the text.

## Tools

- **Plots (line charts, bar charts, scatter plots, etc.)**: use matplotlib by default.
- **Flowcharts and diagrams**: use PowerPoint or Keynote. Do not use Google Slides — the output quality is generally poor. You may use more advanced tools (e.g., Illustrator), but PowerPoint is already good enough.

## AI Usage

- **Do not over-rely on AI for figure making.**
- **Never use AI to generate flowcharts or diagrams.** Make them manually. AI may only assist with small, isolated parts.
