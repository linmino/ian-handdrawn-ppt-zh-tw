# Ian Handdrawn PPT

> 把文章、課程筆記、提綱或已有材料，變成一套繁體中文手繪技術解釋風格的 PPT-style 頁面圖。
>
> 21:9 封面 | 16:9 正文配圖 | PNG 輸出 | 適合文章配圖、課程課件、知識卡片和技術概念解釋

---

## 這個倉庫是什麼

Ian Handdrawn PPT 是一個 Codex Skill，用來指導 AI Agent 把內容整理成**繁體中文手繪技術解釋圖**。

它不是傳統 PPT 模板，也不是可編輯 PPTX 生成器。它的目標是產出可以直接用於文章、課程、分享稿裡的**整頁 PNG 視覺圖**：

- 先理解材料，提煉敘事結構
- 再把每一頁對映到合適的語義版式
- 統一鎖定手繪視覺 DNA
- 每頁生成一張完整 raster image
- 多頁時生成 contact sheet 方便快速檢查

一句話：**讓 AI 不只是“做幾頁 PPT”，而是先想清楚內容，再生成一組有統一風格的中文技術解釋圖。**

推薦生圖模型：**最好使用 ChatGPT Image 2.0**。如果當前環境沒有這個模型，就使用可用的最高質量影像模型，並儘量讓整套圖保持同一個模型、同一套 style lock。

---

## 適合誰用

特別適合：

- 寫中文技術文章，需要封面圖和正文配圖的人
- 做課程、訓練營、工作坊，需要解釋複雜概念的人
- 想把長文、提綱、講稿變成視覺化頁面的人
- 用 Codex 做內容生產，希望減少“模板 PPT 味”的人
- 想讓 AI 先規劃頁面敘事，再生成影像的人

不適合：

- 想要可編輯 PPTX 原始檔的人
- 想要自動匯出 PDF / PPTX 檔案的人
- 想要複雜動效、互動式網頁或向量圖的人
- 想把大量正文塞進一張圖裡的人

---

## 它會產出什麼

預設輸出：

- 21:9 文章封面圖
- 16:9 正文插圖 / 標準頁面圖
- 多頁 contact sheet
- 簡短 slide blueprint summary

預設不輸出：

- 可編輯 PPTX
- image-based PPTX
- PDF
- Keynote 檔案
- HTML / SVG / canvas 版本

---

## 視覺風格

這個 skill 預設使用 Ian 的中文手繪技術解釋風格：

- 近白紙底，不發黃
- 無整頁邊框
- 細手繪線條和輕微鉛筆排線
- 淡藍、鼠尾草綠、淺桃、淡紫標記
- 中央圖小而精，保留大量空白
- 標題剋制，不做大字海報
- 中文文字短、少、可檢查
- 人物很少，最多一個小讀者/工程師角色

參考圖在：

```text
ian-handdrawn-ppt/assets/reference-handdrawn-article-illustration-style.png
```

---

## 示例效果

下面是一組用 Ian Handdrawn PPT 生成的示例圖：1 張超寬封面 + 3 張正文解釋頁。

### 能自動化不等於該自動化

![能自動化不等於該自動化](examples/images/cover-automation-boundary.png)

### 閱讀其實是兩件事

![閱讀其實是兩件事](examples/images/page-01-reading-two-things.png)

### 自動化該放哪裡

![自動化該放哪裡](examples/images/page-02-where-to-automate.png)

### 三問判斷法

![三問判斷法](examples/images/page-03-three-question-method.png)

---

## 安裝

克隆倉庫：

```bash
git clone https://github.com/helloianneo/ian-handdrawn-ppt.git
cd ian-handdrawn-ppt
```

複製 skill 到 Codex skills 目錄：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R ./ian-handdrawn-ppt "${CODEX_HOME:-$HOME/.codex}/skills/"
```

安裝後，在 Codex 裡使用：

```text
Use $ian-handdrawn-ppt 把這篇文章做成 1 張繁體中文封面圖 + 3 張繁體中文正文配圖。
```

---

## 怎麼用

### 文章封面 + 正文配圖

```text
Use $ian-handdrawn-ppt 把下面這篇文章做成 1 張 21:9 繁體中文封面圖 + 3 張 16:9 繁體中文正文配圖。
風格保持繁體中文手繪技術解釋圖，文字儘量短，每張圖只表達一個觀點。

<貼上文章>
```

### 課程課件頁

```text
Use $ian-handdrawn-ppt 把這份課程大綱整理成 8 頁繁體中文手繪技術課件圖。
面向有基礎的新手，每頁一個核心概念，輸出 slide-by-slide blueprint，然後生成最終 PNG 頁面圖。

<貼上課程大綱>
```

### 只規劃，不生圖

```text
Use $ian-handdrawn-ppt 先不要生圖。
請把這篇內容規劃成一套 10 頁左右的繁體中文手繪技術 PPT-style image deck。
每頁給出標題、主旨、版式 archetype、可見文字和影像 brief。

<貼上素材>
```

更多示例見 [examples/prompts.md](examples/prompts.md)。

---

## 工作流程

這個 skill 的流程是：

1. 讀取材料：文章、Markdown、PDF、DOCX、PPTX、課程大綱、講稿或粗略想法
2. 做 intake：判斷主題、受眾、場景、目標、核心論點和素材充分度
3. 規劃敘事：選擇教學、說服、報告、產品解釋或知識卡片結構
4. 選擇頁面 archetype：封面隱喻、左右對比、流程、迴圈、分類、矩陣、總結等
5. 鎖定視覺 DNA：統一紙底、標題、頁碼、線條、色彩、圖形尺度
6. 每頁單獨寫影像 prompt：包含頁面角色、主旨、構圖和 `Required text only`
7. 生圖並檢查：中文文字、畫幅、風格一致性、是否漂黃、是否過度模板化
8. 多頁生成 contact sheet，最後交付 PNG 頁面圖

---

## 目錄結構

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
├── examples/
│   ├── images/
│   │   ├── cover-automation-boundary.png
│   │   ├── page-01-reading-two-things.png
│   │   ├── page-02-where-to-automate.png
│   │   └── page-03-three-question-method.png
│   └── prompts.md
└── ian-handdrawn-ppt/
    ├── SKILL.md
    ├── assets/
    │   ├── reference-handdrawn-article-illustration-style.png
    │   └── theme-tokens.json
    └── references/
        ├── intake.md
        ├── narrative-planning.md
        ├── output-quality.md
        ├── prompt-patterns.md
        ├── slide-archetypes.md
        └── visual-dna-v6.md
```

真正需要安裝到 Codex 的是子目錄：

```text
ian-handdrawn-ppt/
```

根目錄的 README、LICENSE、NOTICE 和 examples 是 GitHub 分享文件。

---

## 注意事項

- 圖片裡的中文文字越短越穩定。
- 最好每個頁面多生成幾次，再從中挑選中文字、構圖、語義關係都最穩的一張。
- AI 影像模型可能出現錯字、幻覺標籤、物體關係錯誤、風格漂移，不要預設第一張就是最終稿。
- 如果中文渲染失敗，應先減少字數並重生。
- 如果畫面方向已經正確但文字仍錯，可以保留影像方向，再用確定性後處理疊準確中文。
- PPTX/PDF 可以作為輸入素材讀取，但不是這個 skill 的輸出格式。
- 這個 skill 的重點是“內容語義 → 頁面敘事 → 手繪解釋圖”，不是模板套版。

---

## 相關資料

如果你對 AI 工作流、內容創作和個人知識庫感興趣，也可以看這些：

- [Awesome Claude Code Skills](https://github.com/helloianneo/awesome-claude-code-skills) — Claude Code Skills / Agents / Plugins 精選合集
- [Obsidian + Claude AI Second Brain](https://github.com/helloianneo/obsidian-ai-second-brain) — Obsidian + Claude AI 個人知識庫搭建指南
- [Claude Code Handbook](https://github.com/helloianneo/claude-code-handbook) — Claude Code 高階使用指南

---

## 關於作者

**Ian (伊恩)** — 產品設計師 / 一人公司實踐者 / AI Builder

用 AI 團隊打造一人公司。

- X/Twitter: [@ianneo_ai](https://x.com/ianneo_ai)
- 網站: [ianneo.xyz](https://ianneo.xyz)
- 微信: 17855813746
- 郵箱: hello.neoc@gmail.com

> **🚀 正在開啟：內容創作丨AI 工作流圍觀營，歡迎來玩！** 加微信瞭解詳情。

---

## License

MIT License. See [LICENSE](LICENSE).
