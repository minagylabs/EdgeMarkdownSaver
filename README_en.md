<p align="right">
  <a href="README.md">한국어</a> | <b>English</b> | <a href="README_jap.md">日本語</a> | <a href="README_zh_cn.md">简体中文</a> | <a href="README_zh_tw.md">繁體中文</a>
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
  <b>1-Click Microsoft Edge Extension for Saving Math (TeX), Diagrams (Mermaid), Tables & Figures as Markdown</b><br>
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

A Manifest V3 extension for Microsoft Edge that lets you highlight any web content—including rich text, LaTeX equations, Mermaid diagrams, HTML tables, and figures—and save it directly as clean GitHub-Flavored Markdown (`.md`) via Windows' native **Save As** file dialog, or copy it straight to your clipboard.

---

## Key Capabilities

* **Native Windows Save As Dialog**: Launches the genuine Windows file picker (`showSaveFilePicker` with a reliable `chrome.downloads` fallback) pre-filled with the page or section title.
* **TeX & LaTeX Math Preservation**: Detects KaTeX, MathJax (v2/v3), MathML, and arXiv LaTeXML formulas. Formats inline equations as `$inline$` and block equations as `$$\nblock\n$$`. Automatically normalizes special macros like `\mathbbm{1}` into universal `\mathbf{1}` for seamless Markpad and KaTeX compatibility.
* **Mermaid Diagram Extraction & Reconstruction**: Preserves raw code blocks or reconstructs flowcharts and sequence diagrams directly from rendered SVG vector graphs into fenced ```` ```mermaid ```` blocks.
* **GFM Pipe Table Formatting**: Parses HTML `<table>` elements and column alignments (`:---`, `:---:`, `---:`) into standard GitHub-Flavored Markdown pipe tables.
* **Self-Contained Offline Figures (Base64)**: Inlines selected images and `<canvas>` graphics as Base64 Data URIs on demand, allowing the resulting `.md` file to render offline without external image folders.
* **Clipboard Quick Export**: Converts selections and writes Markdown directly to your system clipboard with a subtle on-screen toast confirmation.

---

## Installation

### Security Pre-Check
Before installing scripts or unpacked extensions, please scan your computer with Windows Defender or your preferred security software.

### 1-Click Automated PowerShell Setup
1. Right-click [`install_edge_markdown_saver.ps1`](install_edge_markdown_saver.ps1) and choose **Run with PowerShell** (or run from your terminal):
   ```powershell
   pwsh -ExecutionPolicy Bypass -File .\install_edge_markdown_saver.ps1
   ```
2. The script automatically unpacks all extension files to `$HOME\EdgeMarkdownSaver` and opens Edge's extensions page (`edge://extensions/`).
3. Enable the **Developer mode** toggle in Microsoft Edge's left sidebar.
4. Click **Load unpacked** at the top and select the `$HOME\EdgeMarkdownSaver` folder.

---

## How to Use

1. Highlight any combination of text, tables, equations, diagrams, or figures on a webpage.
2. Right-click the highlighted selection.
3. Select an action under **Save Selection as Markdown**:

| Menu Option | Description |
| :--- | :--- |
| **Save as Markdown (.md)... [Save As Dialog]** | Opens the native Windows Save As dialog pre-filled with the title to save the `.md` file to your chosen directory. |
| **Save as Self-Contained Markdown (Embed Figures as Base64)...** | Embeds selected figures and canvases directly as Base64 Data URIs for offline, self-contained portability. |
| **Copy Selection as Markdown to Clipboard** | Converts the selection and copies Markdown directly to your clipboard. |

---

## Supported Conversions

| Content Type | Input Elements Handled | Markdown Output Format |
| :--- | :--- | :--- |
| **Rich Text & Code** | Headings (`h1`–`h6`), bold, italics, strikethrough, blockquotes, nested lists, tasks, and syntax-highlighted `<pre><code>` | Standard Markdown and fenced code blocks with language tags (```` ```python ````) |
| **Tables** | HTML `<table>`, `<thead>`, `<tbody>`, column alignments (left, center, right), `colspan`, multi-line cells | GitHub-Flavored Markdown (GFM) pipe tables (`\| :--- \| :---: \| ---: \|`) |
| **TeX / LaTeX Math** | KaTeX (`.katex`), MathJax v2/v3 (`<mjx-container>`), MathML (`<math>`), arXiv LaTeXML | Inline `$ ... $` and display `$$\n...\n$$` blocks (normalized with Markpad-compatible `\mathbf{1}`) |
| **Diagrams** | `<pre class="mermaid">`, `<div class="mermaid">`, `data-mermaid`, SVG flowcharts | Fenced ```` ```mermaid ```` blocks |
| **Figures & Images** | `<figure>`, `<figcaption>`, `<img>`, `<picture>`, `<canvas>`, `<object data="...">`, `<svg>` | `![caption](url)` followed by italicized `*Figure caption*` |

---

## Version History

| Version | Date | Key Highlights |
| :---: | :---: | :--- |
| **`v1.0`** | 2026-10-22 | • **Initial Official Release**<br>• 1-Click automated PowerShell installer (`install_edge_markdown_saver.ps1`)<br>• TeX & LaTeX formula detection (KaTeX, MathJax v2/v3, MathML, arXiv LaTeXML)<br>• Universal indicator macro normalization (`\mathbbm{1}` → `\mathbf{1}`) for Markpad and KaTeX<br>• Equation table conversion into standard LaTeX display math blocks with tags (`$$ ... \tag{N} $$`)<br>• Mermaid diagram extraction and SVG flowchart reconstruction<br>• GFM pipe table formatting with automatic column alignment<br>• Self-contained offline Markdown export via Base64 figure and image embedding<br>• Native Windows Save As file dialog (`showSaveFilePicker`) and clipboard export<br>• Zero data collection and ad-free architecture |

---

## Support Minagy Labs

Edge Markdown Saver is a free, open-source tool developed and maintained by **Minagy Labs**. It contains zero advertisements and collects no personal data.

If this tool was helpful to your workflow or research, please consider supporting development:

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

## License & Credits

* **Software**: Released under the [MIT License](LICENSE).
* **Copyright**: Copyright © 2026 **Minagy Labs**. All rights reserved.
