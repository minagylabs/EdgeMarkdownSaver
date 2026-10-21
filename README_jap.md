<p align="right">
  <a href="README.md">한국어</a> | <a href="README_en.md">English</a> | <b>日本語</b> | <a href="README_zh_cn.md">简体中文</a> | <a href="README_zh_tw.md">繁體中文</a>
</p>

# Edge Markdown Saver — エッジ マークダウン セーバー

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="logo/minagy_monogram_coral.png">
    <source media="(prefers-color-scheme: light)" srcset="logo/minagy_monogram.png">
    <img src="logo/minagy_monogram.png" alt="Minagy Labs Logo" width="140" height="140" />
  </picture>
</p>

<p align="center">
  <b>数式(TeX)・図(Mermaid)・表・画像をワンクリックで保存する Microsoft Edge 拡張機能</b><br>
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

ウェブページ上で選択した領域（テキスト、LaTeX 数式、Mermaid ダイアグラム、HTML テーブル、画像）を、GitHub スタイルの Markdown (`.md`) ファイルとして即座に保存またはクリップボードにコピーできる Microsoft Edge 専用の Manifest V3 拡張機能です。

Windows 標準の**名前を付けて保存**ダイアログに対応しており、任意のフォルダに直接保存できます。

---

## 主な機能

* **Windows ネイティブ「名前を付けて保存」**: ページタイトルまたは見出しが自動入力された Windows ファイル保存ダイアログを呼び出します (`showSaveFilePicker` および `chrome.downloads` 自動フォールバック)。
* **TeX / LaTeX 数式の完全保持**: KaTeX、MathJax (v2/v3)、MathML、arXiv LaTeXML を自動検出し、`$inline$` および `$$\nblock\n$$` 形式に変換します。`\mathbbm{1}` などの特殊記号は Markpad や KaTeX 標準の `\mathbf{1}` へ自動正規化されます。
* **Mermaid ダイアグラムの抽出と復元**: コードブロックだけでなく、描画済み SVG のノードやエッジを解析して整った ```` ```mermaid ```` ブロックとして再構築します。
* **GFM パイプテーブルへの変換**: HTML `<table>` の構造や配置属性（`:---`, `:---:`, `---:`）を認識し、標準的な Markdown パイプテーブルへ変換します。
* **オフライン完全自己完結型保存 (Base64)**: 画像や `<canvas>` を Base64 データ URI としてインライン埋め込みし、外部画像フォルダなしで単独表示できる `.md` ファイルを出力します。
* **クリップボードへの高速コピー**: ファイルを作成せず、整形済み Markdown をクリップボードへ直接コピーします。

---

## インストール方法

### 事前セキュリティ確認
スクリプト実行または拡張機能の読み込み前に、Windows Defender やウイルス対策ソフトで PC の安全をご確認ください。

### ワンクリック PowerShell 自動セットアップ
1. [`install_edge_markdown_saver.ps1`](install_edge_markdown_saver.ps1) を右クリックし、**PowerShell で実行**を選択します（またはターミナルから実行）:
   ```powershell
   pwsh -ExecutionPolicy Bypass -File .\install_edge_markdown_saver.ps1
   ```
2. 自動的に `$HOME\EdgeMarkdownSaver` フォルダへ拡張機能ファイルが展開され、Edge の拡張機能ページ (`edge://extensions/`) が開きます。
3. Microsoft Edge の左下にある**開発者モード**をオンにします。
4. ページ上部の**パッケージ化されていない拡張機能を読みこむ**をクリックし、`$HOME\EdgeMarkdownSaver` フォルダを選択します。

---

## 使い方

1. ウェブページ上で保存したいテキスト、表、数式、図、画像などをドラッグして選択します。
2. 選択範囲の上で右クリックします。
3. コンテキストメニューの **Save Selection as Markdown** から実行したい操作を選択します:

| メニュー項目 | 動作説明 |
| :--- | :--- |
| **Save as Markdown (.md)... [Save As Dialog]** | Windows 標準の保存ダイアログを開き、指定したフォルダとファイル名で `.md` ファイルを保存します。 |
| **Save as Self-Contained Markdown (Embed Figures as Base64)...** | 画像とキャンバスを Base64 データ URI として埋め込み、単独でオフライン表示可能な `.md` ファイルとして保存します。 |
| **Copy Selection as Markdown to Clipboard** | 選択範囲を Markdown に変換し、クリップボードに即座にコピーします。 |

---

## 対応フォーマット一覧

| コンテンツ種類 | 解析対象の HTML 要素 | Markdown 出力形式 |
| :--- | :--- | :--- |
| **テキスト & コード** | 見出し(`h1`～`h6`)、太字、斜体、打ち消し線、引用、ネストリスト、タスク、`<pre><code>` | 標準 Markdown および言語タグ付きコードブロック (```` ```python ```` 等) |
| **テーブル (表)** | `<table>`、`<thead>`、`<tbody>`、列揃え（左・中央・右）、`colspan`、複数行セル | GitHub-Flavored Markdown (GFM) パイプテーブル (`\| :--- \| :---: \| ---: \|`) |
| **TeX / LaTeX 数式** | KaTeX(`.katex`)、MathJax v2/v3(`<mjx-container>`)、MathML(`<math>`)、arXiv LaTeXML | インライン `$ ... $` および別行立て `$$\n...\n$$` (Markpad 互換 `\mathbf{1}` 正規化) |
| **ダイアグラム** | `<pre class="mermaid">`、`<div class="mermaid">`、`data-mermaid`、SVG グラフ | Fenced ```` ```mermaid ```` ブロック |
| **画像 & グラフィック** | `<figure>`、`<figcaption>`、`<img>`、`<picture>`、`<canvas>`、`<object data="...">`、`<svg>` | `![説明](url)` および斜体キャプション `*Figure caption*` |

---

## 更新履歴 (Version History)

| バージョン | リリース日 | 主な更新内容 |
| :---: | :---: | :--- |
| **`v1.0`** | 2026-10-22 | • **初回正式リリース**<br>• ワンクリック PowerShell 自動セットアップスクリプト (`install_edge_markdown_saver.ps1`) 提供<br>• TeX / LaTeX 数式検出・変換 (KaTeX、MathJax v2/v3、MathML、arXiv LaTeXML 対応)<br>• Markpad 互換のための `\mathbbm{1}` → `\mathbf{1}` 自動正規化<br>• arXiv 数式テーブルの標準 LaTeX 別行立て数式ブロック (`$$ ... \tag{N} $$`) 変換<br>• Mermaid ダイアグラム抽出および描画済み SVG フローチャート逆復元<br>• GFM パイプテーブルへの自動変換と列揃え配置属性対応<br>• Base64 画像インライン埋め込みによる完全オフライン自己完結型 `.md` 保存<br>• Windows ネイティブ「名前を付けて保存」ダイアログ (`showSaveFilePicker`) およびクリップボードコピー対応<br>• 個人データ収集なし・完全無料オープンソース |

---

## 開発者へのサポート

Edge Markdown Saver は **Minagy Labs** が無償で提供しているオープンソースツールです。広告や有料プランはありません。

日頃の調査や研究・お仕事で役立ちましたら、ぜひ開発の継続をサポートしてください:

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

## ライセンスとクレジット

* **Software**: Released under the [MIT License](LICENSE).
* **Copyright**: Copyright © 2026 **Minagy Labs**. All rights reserved.
