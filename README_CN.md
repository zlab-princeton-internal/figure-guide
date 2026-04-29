[English](README.md)

# 图表制作指南

By [Zhuang Liu](https://liuzhuang13.github.io/).

## 总则

- 一个好的 paper，读者扫一眼几个核心 figure 和 table 就能明白你最重要的 claim 和结论。最多再看一下 caption，最好连 caption 都不用看。如果读者必须读正文才能理解你最重要的图表，说明图表做得不够 clear、context 给得不够。
- 重要的 figure 和 table，caption 一定要足够详细。核心结果的 caption 不能只有一行甚至半行。

## 字体（最常见的问题，请务必做到）

- **流程图和示意图中的文字请使用 Arial（或 Helvetica）。** 不要用衬线字体。
- **图中文字大小应与 caption 接近，可以稍大，但绝对不能比 caption 小很多。** 大部分人犯的错误是字太小，看着非常难受。请在编译后的 PDF 中检查。

以上两条是最频繁反复强调的 feedback。搞对这两条，很多问题就不会出现。

- **示意图/流程图中的文字一般不要加粗。** 加粗不会让文字更清晰，只会更丑。最多只对极少数需要强调的词加粗，不要整类文字都加粗。

## 工作流

- **用 Dropbox 同步 Overleaf**，这样你在本地生成的图会自动同步到 Overleaf，不用每次手动拖拽上传。这会节省大量时间。设置方法见 [Overleaf-Dropbox sync](https://www.overleaf.com/learn/how-to/Dropbox_Synchronization)。

## 格式

- **所有图表导出为 PDF**（矢量图），不要用 PNG/JPG。放大不模糊，文字可选中。
- **如果用 HTML 制作图，PDF 必须是矢量的，不能是光栅的。** 常见错误：HTML 渲染成 PNG 再转 PDF，放大会模糊。正确做法：用 Chrome 的 `--print-to-pdf` 生成真正的矢量 PDF，再用 `pdfcrop` 裁边。示例：`chrome --headless --print-to-pdf=out.pdf --no-pdf-header-footer file.html`，然后 `pdfcrop out.pdf out_cropped.pdf`。
- **裁掉所有白边。** matplotlib 中使用 `plt.savefig(..., bbox_inches='tight')`。HTML 生成的 PDF 用 `pdfcrop`（TeX Live 自带）自动裁边。

## 视觉风格

- 方框/矩形加黑色细边框，看起来更精致。
- 示意图中的箭头用纯黑、细、无边框的样式（PPT 中的默认细箭头即可）。
- **文字和边框默认用纯黑色。** 灰色可以用来表示次要元素（当已经有纯黑作为主色时），但不要一上来最深的颜色就是灰色，会显得像网页而不是学术论文。箭头也一样：用纯黑箭头，不要灰色。
- 方框中的文字大小要和框的大小匹配。文字不能在框内四面都离边很远，至少上下或左右要贴近框边。
- 配色可以考虑深色底 + 白色文字的风格。

> **Fig. 1** — 细箭头 + 黑色细边框 + 深色底白字 + 文字贴合框大小。From [DyT](https://arxiv.org/abs/2503.10622).
>
> <img src="examples/dyt_diagram.png" width="500">

- 尽量去掉无意义的分隔线和边框，可以用背景色块代替（参考 Fig. 5）。
- **注意图与 caption、caption 与正文之间的间距。** 这个间距经常要么太大要么太小，需要手动调整。只要你 aware 这件事，就会调到合适的距离。
- **Caption 必须与正文在视觉上有明显区分。** 使用 `\captionsetup{font=footnotesize}`（或至少 `font=small`），让 caption 明显比正文小一两号。扫一眼页面就应该能区分 caption 和正文，否则页面会显得杂乱、结构不清。
- **图内部不要太松散也不要太拥挤。** 箭头不要太长，box 和 box 之间不要隔太远。箭头应该基本填满两个 box 之间的空隙，不要出现"两个 box 隔很大一段空白、中间只有一小截箭头"的情况。
- **大的 box（比如带颜色的 prompt 框）必须四面封闭，即使跨页也是。** 每一截都要看起来完整。
- 表格去掉所有竖线。

> **反例** — 跨页处缺上下边框。
>
> <img src="examples/bad_box_no_boundary.png" width="700">

> **正例** — 每一截都四面封闭。
>
> <img src="examples/good_box_with_boundary.png" width="700">

## 示意图 / Teaser

- 核心 idea 用一张简单的图表达出来。不要画特别复杂的 pipeline 图（上下三四行、左右几列、每个 component 都有标注和颜色）。越简单越好。
- 可以用对比的方式（旧方法 vs 你的方法），让 idea 一目了然。
- Pipeline/diagram 类的图也可以考虑用 HTML 制作（通过 prompting 修改会更方便），但注意避免典型的 HTML 风格：不要使用粗体文字、全大写短语、灰色分隔线、灰色文字。文字默认用黑色，使用普通大小写，保持学术论文的视觉风格。
- **用 HTML 设计时，先并排提出多个布局方案再做选择。** 在一个 HTML 页面中同时展示 3-4 个平行方案来比较，比每次只改一点要快得多。这适用于布局、配色和元素位置。

> **Fig. 2** — 用一张简洁的图表达整个核心机制。From [MoCo](https://arxiv.org/abs/1911.05722).
>
> <img src="examples/moco_fig1.png" width="300">

> **Fig. 3** — 三种方法并排对比，结构一致，差异一目了然，每个子图单独读也很容易理解。From [MoCo](https://arxiv.org/abs/1911.05722).
>
> <img src="examples/moco_fig2.png" width="700">

> **Fig. 4** — 左右对比，用具体数字演示两种方法的差异，一看就懂。From [Wanda](https://arxiv.org/abs/2306.11695).
>
> <img src="examples/wanda_fig1.png" width="700">

## 内容

- 如果你的工作涉及 vision generation，论文中一定要展示 generation samples，不能只有数值表格和 plot。
- 多放具体的 examples（数据集样本、环境截图、模型输出等），让读者能直观看到你的数据和结果长什么样。尤其是数据相关的工作。

> **Fig. 5** — 用背景色块代替分隔线展示数据样本，配色也可参考。From WorldBench (upcoming).
>
> <img src="examples/colorbox_example.png" width="700">

## 伪代码 / 代码

- 如果你的方法足够简单，考虑加一个伪代码或真实代码（如 PyTorch）来描述核心算法。这对 clarity 很有帮助。
- 方法简单时用真实代码，概念性的用伪代码。

> **Fig. 6** — 直接用 PyTorch 代码描述算法，几行就说清楚了。From [Wanda](https://arxiv.org/abs/2306.11695).
>
> <img src="examples/wanda_algo.png" width="350">

## 布局

- 核心 message 的图应该占整行（full width），不要为了省空间和不相关的图挤在一起。一行图应该只传达一个概念。如果只有一张重要的图，宁可旁边再做一张相关的图凑满一行，也不要把它和无关的 ablation 拼在一起。
- 不重要的图（ablation、side analysis）可以一行放两个。
- 如果实在凑不满一行，用 wrapfigure 嵌在文字旁边，不要硬凑。
- 图表和引用它的文字距离不要超过半页。早期的 figure（如 Figure 1/2）可以为了 framing 往前提，但从实验部分开始要严格靠近引用位置。
- 并排的两张图，中间的间隙要相对于页面居中（或接近居中）。不要因为左图有 y 轴 label/ticks 就把整体往右挤，宁可右边留白或把图缩小一点，保持视觉对称。如果有总标题（caption），也要相对页面居中。
- 并排子图要注意垂直对齐：左右两图包括标题、标注在内的整体视觉重心要平齐。设计时尽量让左右两图的结构一致（都有上方标题，或都没有），避免一边有标题一边没有导致难以对齐。如果 caption 是分开的（如 (a) 和 (b)），caption 的第一行要对齐，行数也尽量接近。
- 避免在页面顶部放一张窄/稀疏的小图，两侧留大片空白。如果一张图不能填满栏宽或页宽，要么用 wrapfigure 嵌在文字旁边，要么放在页面中部有上下文环绕的位置。
- 绝对不能有连续两页没有任何图表。一页没有图表的情况也要尽量少。

## 多样性与节奏

- 图表类型要有 variety：折线图、柱状图、heatmap、示意图等混合使用，不要全是同一种。表格大小也应有些变化。但不要为了变化而强行变化，自然为主。
- 图和表在论文中要穿插分布，不要某一页全是图、另一页全是表。整体要有节奏感和美感。
- **不同类型的视觉元素要穿插全文。** 不要开头一个大图，后面全是表格和折线图。即使是彩色的表格连续看也会疲劳，要混合图片、qualitative samples、示意图等。
- 可参考 [Cambrian-1](https://arxiv.org/abs/2406.16860) 等论文的图表编排。

## Plot（matplotlib）

- Plot 默认使用 matplotlib。
- 折线图、scatter plot 等一般应该是宽略大于高的矩形，不要用正方形，更不要高大于宽。微微偏胖一点比较好看。
- 折线图考虑加很淡的虚线网格作为背景，增加结构感，方便读者读取数值。
- Y 轴刻度必须是整数。不要让 matplotlib 自动生成刻度值（如 30.3, 71.1, 96.9），手动设置为整数（如 30, 50, 70）。
- 柱状图的 bar 一定要用纯粹的矩形，不要用圆角。
- 配色要反复调整，不要随意选。可以参考 DyT 和 MoCo 论文的配色方案，以及 Fig. 5 中的彩色背景块配色（实际使用可适当调浅）。（后续会补充推荐配色。）
- Heatmap 的配色不容易调好，下面是一个可参考的配色方案。

> **Fig. 7** — Heatmap 配色参考（红黄绿方案）。From WorldBench (upcoming).
>
> <img src="examples/heatmap_example.png" width="450">

## 引用

- 所有图表在正文中至少引用一次。

## 工具

- **Plot（折线图、柱状图、scatter plot 等）**：默认使用 matplotlib。
- **流程图和示意图**：可以用代码（HTML/CSS 或 Python）通过 Claude Code 制作和迭代，方便协作和版本管理。代码源文件和 PDF 一起存到 repo。也可以用 PowerPoint 或 Keynote 手动制作。不要用 Google Slides，出图质量一般不好。

## AI 使用

- 不要过度依赖 AI 直接生成图片（如 vision generation 类的图）。
- 流程图和 diagram 可以考虑用 coding 的方式（如 HTML）制作，通过 prompting 迭代。手动制作（PowerPoint/Keynote）也是可靠的选择。
