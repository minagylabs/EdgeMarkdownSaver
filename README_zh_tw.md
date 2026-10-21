<p align="right">
  <a href="README.md">한국어</a> | <a href="README_en.md">English</a> | <a href="README_jap.md">日本語</a> | <a href="README_zh_cn.md">简体中文</a> | <b>繁體中文</b>
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
  <b>一鍵儲存數學公式 (TeX)、圖表 (Mermaid)、表格與圖片為 Markdown 的 Microsoft Edge 擴充功能</b><br>
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

專為 Microsoft Edge 打造的 Manifest V3 擴充功能。支援選取網頁任何內容（富文字、LaTeX 數學公式、Mermaid 圖表、HTML 表格及圖片），並透過 Windows 原生**另存新檔**檔案選擇器直接匯出為標準的 GitHub 風格 Markdown (`.md`) 檔案，或一鍵複製至系統剪貼簿。

---

## 核心特色

* **Windows 原生「另存新檔」對話方塊**：自動帶入網頁或章節標題，叫用原生 Windows 檔案選擇器（`showSaveFilePicker` 並具備可靠的 `chrome.downloads` 自動遞補相容機制）。
* **TeX / LaTeX 數學公式完整保留**：精準偵測 KaTeX、MathJax (v2/v3)、MathML 與 arXiv LaTeXML 公式，標準化轉換為行內 `$inline$` 與區塊 `$$\nblock\n$$` 格式。針對 `\mathbbm{1}` 等特殊符號，自動正規化為與 Markpad 及 KaTeX 完美相容的 `\mathbf{1}`。
* **Mermaid 圖表擷取與重建**：完整保留原始程式碼區塊，並能從已繪製的 SVG 向量圖中解析節點與連線，重建為標準 ```` ```mermaid ```` 程式碼區塊。
* **GFM 管道表格自動排版**：解析 HTML `<table>` 結構與對齊屬性（`:---`、`:---:`、`---:`），轉換為標準 GitHub 風格 Markdown 表格。
* **離線單一檔案支援 (Base64 圖片內嵌)**：可依需求將選取的圖片與 `<canvas>` 畫布以 Base64 Data URI 格式內嵌至文件，產生無須依賴額外圖片資料夾即可離線檢視的單一 `.md` 檔案。
* **剪貼簿極速複製**：直接將選取內容轉換為 Markdown 並寫入剪貼簿，附帶優雅的浮動提示。

---

## 安裝方式

### 安裝前安全性檢查
在執行指令碼或載入未封裝擴充功能前，建議先使用 Windows Defender 或您慣用的防毒軟體掃描電腦。

### 一鍵 PowerShell 自動化安裝
1. 在 [`install_edge_markdown_saver.ps1`](install_edge_markdown_saver.ps1) 上按一下滑鼠右鍵，選擇 **使用 PowerShell 執行**（或在終端機中執行）：
   ```powershell
   pwsh -ExecutionPolicy Bypass -File .\install_edge_markdown_saver.ps1
   ```
2. 指令碼會自動將擴充功能檔案釋放至 `$HOME\EdgeMarkdownSaver` 資料夾，並開啟 Edge 的擴充功能管理頁面 (`edge://extensions/`)。
3. 開啟 Microsoft Edge 左側面板的 **開發人員模式** 開關。
4. 按一下頂端的 **載入解壓縮**，並選擇 `$HOME\EdgeMarkdownSaver` 資料夾。

---

## 使用方式

1. 在網頁上拖曳滑鼠選取欲儲存的文字、表格、公式、圖表或圖片。
2. 在選取範圍上方按一下滑鼠右鍵。
3. 在右鍵選單中尋找 **Save Selection as Markdown** 並點選需要的動作：

| 功能選項 | 說明 |
| :--- | :--- |
| **Save as Markdown (.md)... [Save As Dialog]** | 叫用 Windows 原生另存新檔對話方塊，將 `.md` 檔案儲存至指定的資料夾與檔名。 |
| **Save as Self-Contained Markdown (Embed Figures as Base64)...** | 將選取的圖片與畫布直接轉換為 Base64 Data URI 內嵌，輸出完全離線獨立的單一 `.md` 檔案。 |
| **Copy Selection as Markdown to Clipboard** | 將選取的內容直接轉換為 Markdown 並複製到系統剪貼簿。 |

---

## 支援轉換格式

| 內容類型 | 支援解析之 HTML 元素 | Markdown 輸出格式 |
| :--- | :--- | :--- |
| **格式化文字與程式碼** | 標題 (`h1`–`h6`)、粗體、斜體、刪除線、引用區塊、巢狀清單、工作清單、語法反白 `<pre><code>` | 標準 Markdown 語法及包含語言標籤的程式碼區塊 (```` ```python ```` 等) |
| **表格** | HTML `<table>`、`<thead>`、`<tbody>`、欄位對齊（靠左/置中/靠右）、`colspan`、多行儲存格 | GitHub 風格 Markdown (GFM) 管道表格 (`\| :--- \| :---: \| ---: \|`) |
| **TeX / LaTeX 數學公式** | KaTeX (`.katex`)、MathJax v2/v3 (`<mjx-container>`)、MathML (`<math>`)、arXiv LaTeXML | 行內 `$ ... $` 與區塊 `$$\n...\n$$` (自動正規化為相容 Markpad 的 `\mathbf{1}`) |
| **圖表與流程圖** | `<pre class="mermaid">`、`<div class="mermaid">`、`data-mermaid`、SVG 向量圖 | 標準 ```` ```mermaid ```` 程式碼區塊 |
| **圖片與圖表插圖** | `<figure>`、`<figcaption>`、`<img>`、`<picture>`、`<canvas>`、`<object data="...">`、`<svg>` | `![圖片說明](url)` 及斜體圖說 `*Figure caption*` |

---

## 版本歷史 (Version History)

| 版本 | 日期 | 主要更新內容 |
| :---: | :---: | :--- |
| **`v1.0`** | 2026-10-22 | • **首次正式發行**<br>• 提供一鍵 PowerShell 自動化安裝指令碼 (`install_edge_markdown_saver.ps1`)<br>• 精準偵測並轉換 TeX / LaTeX 數學公式 (支援 KaTeX、MathJax v2/v3、MathML、arXiv LaTeXML)<br>• 自動正規化特殊符號 (`\mathbbm{1}` → `\mathbf{1}`)，完美相容 Markpad 與 KaTeX<br>• 將 arXiv 公式表格排版轉換為標準 LaTeX 區塊公式 (`$$ ... \tag{N} $$`)<br>• Mermaid 圖表原始碼擷取及已繪製 SVG 向量圖逆向重建<br>• GitHub 風格 Markdown (GFM) 管道表格自動排版與欄位對齊<br>• 支援 Base64 圖片內嵌，匯出完全離線獨立之單一 `.md` 檔案<br>• 叫用 Windows 原生「另存新檔」對話方塊 (`showSaveFilePicker`) 及剪貼簿極速複製<br>• 零資料收集、無廣告純淨開源架構 |

---

## 支持 Minagy Labs

Edge Markdown Saver 是由 **Minagy Labs** 開發與維護的免費開源工具，絕無廣告且不收集任何個人資料。

若此工具有助於您的研究、學習或工作流程，歡迎贊助支持我們的持續開發：

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

## 授權條款與版權聲明

* **軟體專案**: 採用 [MIT License](LICENSE) 授權條款釋出。
* **版權聲明**: Copyright © 2026 **Minagy Labs**. 版權所有。
