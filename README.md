<p align="right">
  <b>한국어</b> | <a href="README_en.md">English</a> | <a href="README_jap.md">日本語</a> | <a href="README_zh_cn.md">简体中文</a> | <a href="README_zh_tw.md">繁體中文</a>
</p>

# Edge Markdown Saver — 엣지 마크다운 세이버

<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="logo/minagy_monogram_coral.png">
    <source media="(prefers-color-scheme: light)" srcset="logo/minagy_monogram.png">
    <img src="logo/minagy_monogram.png" alt="Minagy Labs Logo" width="140" height="140" />
  </picture>
</p>

<p align="center">
  <b>수식(TeX), 다이어그램(Mermaid), 표, 이미지를 원클릭으로 저장하는 엣지 확장 프로그램</b><br>
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
  <a href="https://ctee.kr/place/minagy"><img src="https://img.shields.io/badge/CTEE-후원-FF5B1A.svg?style=flat-square" alt="CTEE"></a>
  <a href="https://www.instagram.com/minagylabs/"><img src="https://img.shields.io/badge/Instagram-@minagylabs-E4405F.svg?style=flat-square" alt="Instagram"></a>
</p>

---

웹페이지에서 마우스로 드래그한 영역(텍스트, LaTeX 수식, Mermaid 다이어그램, HTML 표, 이미지)을 깃허브 스타일 마크다운(`.md`) 파일로 즉시 저장하거나 클립보드에 복사할 수 있는 Microsoft Edge 전용 Manifest V3 확장 프로그램입니다.

Windows 기본 **다른 이름으로 저장** 파일 선택창을 지원하여 원하는 경로에 바로 저장할 수 있습니다.

---

## 주요 기능

* **Windows 네이티브 '다른 이름으로 저장'**: 웹페이지 제목 또는 섹션 제목이 자동으로 입력된 Windows 파일 저장 대화상자를 호출합니다 (`showSaveFilePicker` 및 `chrome.downloads` 자동 폴백).
* **TeX / LaTeX 수식 완벽 보존**: KaTeX, MathJax(v2/v3), MathML, arXiv LaTeXML 수식을 감지하여 `$inline$` 및 `$$\nblock\n$$` 표준 문법으로 변환합니다. `\mathbbm{1}` 등 특수 인디케이터 기호를 Markpad / KaTeX 표준 `\mathbf{1}`로 자동 호환 처리합니다.
* **Mermaid 다이어그램 추출 및 복원**: 코드 블록은 물론 렌더링된 SVG 다이어그램의 노드와 엣지를 분석하여 ```` ```mermaid ```` 블록으로 깔끔하게 복원합니다.
* **GFM 파이프 표 자동 변환**: HTML `<table>` 구조와 열 정렬 속성(`:---`, `:---:`, `---:`)을 분석하여 깃허브 표준 파이프 테이블로 변환합니다.
* **오프라인 자립형 마크다운 지원 (Base64)**: 선택 영역의 이미지와 `<canvas>` 그래픽을 Base64 데이터 URI로 인라인 임베딩하여 별도 이미지 폴더 없이 오프라인에서 열람 가능한 단일 `.md` 파일로 저장합니다.
* **클립보드 빠른 복사**: 별도 파일 저장 없이 클립보드로 마크다운을 즉시 복사합니다.

---

## 설치 방법

### 사전 보안 검사
확장 프로그램 설치 전 Windows Defender 또는 백신 프로그램으로 PC를 사전 검사하여주세요.

### 1클릭 파워셸 자동 설치
1. [`install_edge_markdown_saver.ps1`](install_edge_markdown_saver.ps1) 파일을 마우스 우클릭한 후 **PowerShell에서 실행**을 선택합니다 (또는 터미널에서 실행):
   ```powershell
   pwsh -ExecutionPolicy Bypass -File .\install_edge_markdown_saver.ps1
   ```
2. 자동으로 `$HOME\EdgeMarkdownSaver` 폴더에 확장 프로그램 파일이 생성되고 Microsoft Edge 확장 프로그램 관리 페이지(`edge://extensions/`)가 열립니다.
3. Microsoft Edge 좌측 하단의 **개발자 모드** 토글을 켭니다.
4. 상단의 **확장 패키지 압축을 풉니다** 버튼을 클릭하고 `$HOME\EdgeMarkdownSaver` 폴더를 선택합니다.

---

## 사용 방법

1. 웹페이지에서 저장하고 싶은 텍스트, 표, 수식, 다이어그램, 이미지를 드래그하여 선택합니다.
2. 선택 영역 위에서 마우스 우클릭을 합니다.
3. **Save Selection as Markdown** 메뉴에서 원하는 방식을 선택합니다:

| 메뉴 항목 | 동작 설명 |
| :--- | :--- |
| **Save as Markdown (.md)... [Save As Dialog]** | Windows 네이티브 파일 저장 대화상자를 열어 원하는 폴더와 파일명으로 `.md` 파일을 저장합니다. |
| **Save as Self-Contained Markdown (Embed Figures as Base64)...** | 선택된 이미지와 캔버스를 Base64 Data URI로 인라인 임베딩하여 외부 파일 없이 독립 실행되는 `.md` 파일로 저장합니다. |
| **Copy Selection as Markdown to Clipboard** | 선택 영역을 마크다운으로 변환하여 클립보드에 즉시 복사합니다. |

---

## 지원 변환 형식

| 콘텐츠 유형 | 처리 대상 HTML 요소 | 마크다운 출력 형식 |
| :--- | :--- | :--- |
| **텍스트 & 코드** | 제목(`h1`~`h6`), 굵게, 기울임, 취소선, 인용문, 중첩 목록, 할 일 체크박스, `<pre><code>` | 표준 마크다운 및 언어 태그가 포함된 코드 블록 (```` ```python ```` 등) |
| **표 (Tables)** | `<table>`, `<thead>`, `<tbody>`, 열 정렬(좌, 중, 우), `colspan`, 여러 줄 셀 | GitHub-Flavored Markdown (GFM) 파이프 테이블 (`\| :--- \| :---: \| ---: \|`) |
| **TeX / LaTeX 수식** | KaTeX(`.katex`), MathJax v2/v3(`<mjx-container>`), MathML(`<math>`), arXiv LaTeXML | 인라인 `$ ... $` 및 디스플레이 블록 `$$\n...\n$$` (Markpad 호환 `\mathbf{1}` 자동 변환) |
| **다이어그램** | `<pre class="mermaid">`, `<div class="mermaid">`, `data-mermaid`, SVG 플로우차트 | Fenced ```` ```mermaid ```` 블록 |
| **이미지 & 그래픽** | `<figure>`, `<figcaption>`, `<img>`, `<picture>`, `<canvas>`, `<object data="...">`, `<svg>` | `![설명](url)` 및 캡션 기울임 `*Figure caption*` |

---

## 버전 기록 (Version History)

| 버전 | 일자 | 주요 내용 |
| :---: | :---: | :--- |
| **`v1.0`** | 2026-10-22 | • **최초 공식 릴리스**<br>• 원클릭 PowerShell 자동 설치 스크립트(`install_edge_markdown_saver.ps1`) 제공<br>• KaTeX, MathJax, MathML, arXiv LaTeXML 수식 자동 감지 및 변환<br>• Markpad 및 KaTeX 호환을 위한 `\mathbbm{1}` → `\mathbf{1}` 자동 정규화<br>• arXiv 수식 테이블(`ltx_eqn_table`)의 표준 LaTeX 디스플레이 블록(`$$ ... \tag{N} $$`) 변환<br>• Mermaid 다이어그램 추출 및 렌더링된 SVG 벡터 역복원<br>• GitHub-Flavored Markdown(GFM) 파이프 표 자동 변환 및 열 정렬<br>• Base64 인라인 이미지 임베딩을 통한 완전 오프라인 자립형 `.md` 저장<br>• Windows 네이티브 '다른 이름으로 저장' 대화상자(`showSaveFilePicker`) 및 클립보드 복사 지원<br>• 개인정보 수집 없는 제로 데이터 보안 아키텍처 |

---

## 개발자 후원

Edge Markdown Saver는 **Minagy Labs**에서 무료로 배포하는 오픈소스 도구입니다. 광고나 유료 결제 없이 운영되고 있습니다.

본 프로그램이 일상과 연구/업무에 도움이 되었다면 개발팀을 응원해 주세요:

<p align="center">
  <a href="https://buymeacoffee.com/minagylabs" target="_blank">
    <img src="https://cdn.buymeacoffee.com/buttons/v2/default-yellow.png" alt="Buy Me A Coffee" width="200" />
  </a>
</p>

* **크티 (CTEE)**: [ctee.kr/place/minagy](https://ctee.kr/place/minagy)
* **Buy Me a Coffee**: [buymeacoffee.com/minagylabs](https://buymeacoffee.com/minagylabs)
* **Instagram**: [@minagylabs](https://www.instagram.com/minagylabs/)
* **GitHub Issues**: [minagylabs/EdgeMarkdownSaver/issues](https://github.com/minagylabs/EdgeMarkdownSaver/issues)
* **Email**: `minagylabs@gmail.com`

---

## 라이선스 및 크레딧

* **Software**: Released under the [MIT License](LICENSE).
* **Copyright**: Copyright © 2026 **Minagy Labs**. All rights reserved.
