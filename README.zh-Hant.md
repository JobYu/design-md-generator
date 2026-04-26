# design-md-generator

**語言：** [English](./README.md) · 繁體中文（本頁）

依專案脈絡、網站 URL、設計截圖或引導式訪談，產出符合 [Google Stitch DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) 精神的完整設計系統文件與預覽資產。內建 58 個品牌案例可作為參考起點。

## 什麼是 DESIGN.md？

[DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) 是以 **純 Markdown** 描述產品視覺與互動規則的設計系統文件，讓 AI 編碼代理或設計工具能一致地生成介面，無需 Figma 匯出或額外 schema。


| 檔案          | 誰讀取     | 定義內容       |
| ----------- | ------- | ---------- |
| `AGENTS.md` | 編碼代理    | 如何建置專案     |
| `DESIGN.md` | 設計／編碼代理 | 產品應有的外觀與體感 |


社群策展可參考 **[Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)**：從真實網站萃取、可直接複製的 `DESIGN.md` 與 `preview.html`／`preview-dark.html` 範本庫。  
**本倉庫**則提供 **「從零生成」** 的代理流程、章節模板，以及 **58 個可直接參考的品牌案例**。

## 四種生成模式

Skill 會自動偵測你的輸入類型，並選擇最適合的模式：

| 模式 | 輸入 | 作用 |
|------|------|------|
| **自主模式** | 現有專案檔案（`README.md`、`package.json`、樣式檔） | 分析脈絡並自動生成 DESIGN.md |
| **URL 分析** | 網站網址（`https://...`） | 從實際網頁提取顏色、字體、元件與布局 |
| **圖片分析** | 設計截圖或 Mockup | 從設計圖片識別視覺元素 |
| **引導模式** | 文字描述或無輸入 | 逐步訪談產品氣質與限制 |

若 URL／圖片分析的資料不完整，Skill 會自動進入 **引導式補全**——只問缺失的欄位，而非從頭問完整套問題。

## 倉庫結構

```
design-md-generator/
├── SKILL.md                    # 核心 Skill 編排器（< 500 行）
├── references/                 # 詳細指令與模板（按需載入）
│   ├── modes.md                # 四種模式的詳細提取／訪談流程
│   ├── master-template.md      # DESIGN.md 模板（九章）＋行動 App 擴充
│   └── output-specs.md         # 預覽 HTML 規格、README 模板、原生片段
└── examples/                   # 58 個匿名化設計系統參考案例
    ├── brand-01/
    ├── brand-02/
    ├── brand-03/
    └── ... (brand-01 ~ brand-58，各含一份 DESIGN.md)
```

### 內建範例（`examples/`）

`examples/` 目錄收錄了 **58 個匿名化設計系統參考案例**，源自真實網站的公開視覺風格觀察。每個子目錄（`brand-01` ~ `brand-58`）包含一份 `DESIGN.md`，品牌標識已移除。用途包括：

- **格式參考** — 觀察優質 DESIGN.md 的結構與寫法
- **改寫起點** — 依此結構為自有產品編寫設計系統
- **學習素材** — 建立對顏色、字體、元件規格的直覺

> **注意：** 這些文件是對公開可見設計模式的觀察性分析，非官方品牌設計系統。所有品牌名稱已匿名化以避免商標問題。

## 使用方式

1. 將本倉庫的 `SKILL.md` 依你的 Agent Skill 系統安裝或引用（路徑依你的技能目錄設定而定）。
2. 在對話中使用觸發語：
   - **「生成 DESIGN.md」**
   - **「分析這個網站設計」** / **"design from url"**
   - **「從這張圖片生成設計系統」** / **"design from image"**
   - **「產品視覺規範」** / **"design system document"**
   （完整列表見 `SKILL.md` 前端的 `triggers`）
3. Skill 會自動偵測輸入類型並進入對應模式。
4. 依預設，於專案的 `design-system/`（或你指定的根目錄）取得 `DESIGN.md`、`README.md`（品牌向簡介）、`preview.html`、`preview-dark.html` 等產出。

## 與 awesome-design-md 的分工

| | [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | **本專案（design-md-generator）** |
| --- | --- | --- |
| 定位 | 策展現成 DESIGN.md + 預覽 HTML | 代理流程 + 模板 + 58 個內建範例 |
| 適用 | 快速對齊知名產品視覺語言 | 自有品牌、URL／圖片提取、訪談與反模板化（避免「AI 味」預設） |

兩者都服務同一個目標：**讓 `DESIGN.md` 成為代理可讀、可執行的單一真相來源。**

## 延伸資源

- [Stitch：DESIGN.md 概覽](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Stitch：DESIGN.md 格式說明](https://stitch.withgoogle.com/docs/design-md/format/)
- [VoltAgent／Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)
- [自訂 DESIGN.md 請求（getdesign.md）](https://getdesign.md/request)

## 授權

本倉庫以 [MIT License](./LICENSE) 授權。使用社群範本或第三方 `DESIGN.md` 時，請遵守各來源條款。
