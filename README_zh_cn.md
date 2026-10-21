<p align="right">
  <a href="README.md">한국어</a> | <a href="README_en.md">English</a> | <a href="README_jap.md">日本語</a> | <b>简体中文</b> | <a href="README_zh_tw.md">繁體中文</a>
</p>

# Edge Markdown Saver

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="logo/minagy_monogram_coral.png">
    <source media="(prefers-color-scheme: light)" srcset="logo/minagy_monogram.png">
    <img src="logo/minagy_monogram.png" alt="Minagy Labs Logo" width="140" height="140" />
  </picture>
</p>

<p align="center">
  <b>一键保存数学公式 (TeX)、图表 (Mermaid)、表格与插图为 Markdown 的 Microsoft Edge 扩展</b><br>
  Built by <b>Minagy Labs</b>
</p>

<p align="center">
  <a href="https://github.com/minagylabs/EdgeMarkdownSaver"><img src="https://komarev.com/ghpvc/?username=minagylabs-EdgeMarkdownSaver&label=Visitors&color=238636&style=flat-square" alt="Visitors"></a>
  <a href="https://github.com/minagylabs/EdgeMarkdownSaver/releases/latest"><img src="https://img.shields.io/badge/Release-v1.0-238636.svg?style=flat-square" alt="Release"></a>
  <a href="https://github.com/minagylabs/EdgeMarkdownSaver/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-blue.svg?style=flat-square" alt="License"></a>
  <img src="https://img.shields.io/badge/Platform-Microsoft%20Edge%20%7C%20Windows-0078D6.svg?style=flat-square" alt="Platform">
  <img src="https://img.shields.io/badge/Manifest-V3-informational.svg?style=flat-square" alt="Manifest V3">
  <img src="https://img.shields.io/badge/Security-Zero%20Data%20Collection-9cf.svg?style=flat-square" alt="Security">
  <a href="https://buymeacoffee.com/minagylabs"><img src="https://img.shields.io/badge/Buy%20Me%20a%20Coffee-Support-yellow.svg?style=flat-square" alt="Buy Me a Coffee"></a>
  <a href="https://www.instagram.com/minagylabs/"><img src="https://img.shields.io/badge/Instagram-@minagylabs-E4405F.svg?style=flat-square" alt="Instagram"></a>
</p>

---

一款专为 Microsoft Edge 设计的 Manifest V3 扩展程序。支持划选网页任意内容（富文本、LaTeX 数学公式、Mermaid 图表、HTML 表格及图像插图），并通过 Windows 原生**另存为**文件对话框直接导出为规整的 GitHub 风格 Markdown (`.md`) 文件，或一键复制到系统剪贴板。

---

## 核心特性

* **Windows 原生“另存为”对话框**：自动预填网页或小节标题，调出原生 Windows 文件选择器（`showSaveFilePicker` 并具备可靠的 `chrome.downloads` 自动降级保障）。
* **TeX / LaTeX 数学公式精准保留**：智能识别 KaTeX、MathJax (v2/v3)、MathML 及 arXiv LaTeXML 公式，标准化转换为行内 `$inline$` 与块级 `$$\nblock\n$$` 格式。针对 `\mathbbm{1}` 等指示函数特殊宏，自动规整为与 Markpad 及 KaTeX 完美兼容的 `\mathbf{1}`。
* **Mermaid 图表提取与重构**：不仅完整保留原生代码块，更可从已渲染的 SVG 矢量图形中分析节点与连接关系，重构为标准 ```` ```mermaid ```` 代码块。
* **GFM 管道表格自动排版**：解析 HTML `<table>` 结构及列对齐属性（`:---`、`:---:`、`---:`），转换为规整的 GitHub 风格 Markdown 管道表格。
* **离线独立 Markdown 支持 (Base64 图表内联)**：可按需将选中的图片和 `<canvas>` 画布以 Base64 Data URI 形式嵌入文件，生成无需依赖外部图片目录即可完全离线查看的单个 `.md` 文档。
* **剪贴板极速复制**：将划选内容一键转换为 Markdown 并写入剪贴板，伴有轻量级悬浮提示。

---

## 安装方法

### 安全预检提示
在运行脚本或安装未打包扩展前，建议先使用 Windows Defender 或您信任的防病毒软件扫描电脑。

### 一键 PowerShell 自动化安装
1. 右键单击 [`install_edge_markdown_saver.ps1`](install_edge_markdown_saver.ps1) 文件并选择 **使用 PowerShell 运行**（或在终端中运行）：
   ```powershell
   pwsh -ExecutionPolicy Bypass -File .\install_edge_markdown_saver.ps1
   ```
2. 脚本将自动将扩展文件释放至 `$HOME\EdgeMarkdownSaver` 目录，并打开 Edge 扩展管理页面 (`edge://extensions/`)。
3. 开启 Microsoft Edge 左侧边栏的 **开发人员模式** 开关。
4. 点击顶部的 **加载解压缩的扩展**，并选择 `$HOME\EdgeMarkdownSaver` 文件夹。

---

## 使用指南

1. 在网页上划选需要保存的文字、表格、公式、图表或图片。
2. 在选区上方右键单击。
3. 在右键菜单中找到 **Save Selection as Markdown** 并选择所需操作：

| 菜单项 | 说明 |
| :--- | :--- |
| **Save as Markdown (.md)... [Save As Dialog]** | 调出 Windows 原生另存为对话框，将 `.md` 文件保存到指定路径与文件名。 |
| **Save as Self-Contained Markdown (Embed Figures as Base64)...** | 将选中图像与画布转换为 Base64 Data URI 直接嵌入，生成完全离线独立的 `.md` 文件。 |
| **Copy Selection as Markdown to Clipboard** | 将划选内容转换为 Markdown 并直接复制至剪贴板。 |

---

## 支持的转换格式

| 内容类型 | 识别处理的 HTML 元素 | Markdown 输出格式 |
| :--- | :--- | :--- |
| **富文本与代码** | 标题 (`h1`–`h6`)、粗体、斜体、删除线、引用块、多级列表、待办事项、语法高亮 `<pre><code>` | 标准 Markdown 语法及带语言标识的代码块 (```` ```python ```` 等) |
| **表格** | HTML `<table>`、`<thead>`、`<tbody>`、列对齐属性（左/中/右）、`colspan`、多行单元格 | GitHub 风格 Markdown (GFM) 管道表格 (`\| :--- \| :---: \| ---: \|`) |
| **TeX / LaTeX 数学公式** | KaTeX (`.katex`)、MathJax v2/v3 (`<mjx-container>`)、MathML (`<math>`)、arXiv LaTeXML | 行内 `$ ... $` 与块级 `$$\n...\n$$` (自动规整 Markpad 兼容 `\mathbf{1}`) |
| **流程图与图表** | `<pre class="mermaid">`、`<div class="mermaid">`、`data-mermaid`、SVG 矢量图 | 标准 ```` ```mermaid ```` 代码块 |
| **图像与图表插图** | `<figure>`、`<figcaption>`、`<img>`、`<picture>`、`<canvas>`、`<object data="...">`、`<svg>` | `![插图描述](url)` 及斜体图注 `*Figure caption*` |

---

## 版本历史 (Version History)

| 版本 | 日期 | 主要更新内容 |
| :---: | :---: | :--- |
| **`v1.0`** | 2026-10-22 | • **首次正式发布**<br>• 提供一键 PowerShell 自动化安装脚本 (`install_edge_markdown_saver.ps1`)<br>• 智能识别并转换 TeX / LaTeX 数学公式 (支持 KaTeX、MathJax v2/v3、MathML、arXiv LaTeXML)<br>• 自动规整特殊指示函数宏 (`\mathbbm{1}` → `\mathbf{1}`)，完美兼容 Markpad 与 KaTeX<br>• 将 arXiv 公式表格排版转换为标准 LaTeX 块级公式 (`$$ ... \tag{N} $$`)<br>• Mermaid 图表源码提取及已渲染 SVG 矢量图逆向重构<br>• GitHub 风格 Markdown (GFM) 管道表格自动排版与列对齐<br>• 支持 Base64 图表内联，导出完全离线自包含的单文件 `.md`<br>• 调出 Windows 原生“另存为”文件选择器 (`showSaveFilePicker`) 及剪贴板极速复制<br>• 零数据收集、无广告纯净开源架构 |

---

## 支持 Minagy Labs

Edge Markdown Saver 是由 **Minagy Labs** 维护的开源免费工具，无广告且绝不收集任何个人数据。

如果这款工具对您的学习、研究或日常工作有所帮助，欢迎支持我们的持续开发：

<p align="center">
  <a href="https://buymeacoffee.com/minagylabs" target="_blank">
    <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="200" />
  </a>
</p>

* **Buy Me a Coffee**: [buymeacoffee.com/minagylabs](https://buymeacoffee.com/minagylabs)
* **Instagram**: [@minagylabs](https://www.instagram.com/minagylabs/)
* **GitHub Issues**: [minagylabs/EdgeMarkdownSaver/issues](https://github.com/minagylabs/EdgeMarkdownSaver/issues)
* **Email**: `minagylabs@gmail.com`

---

## 许可证与致谢

* **软件代码**: 采用 [MIT License](LICENSE) 开源协议。
* **版权所有**: Copyright © 2026 **Minagy Labs**. 保留所有权利。
