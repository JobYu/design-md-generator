# design-md-generator

**語言：** [English](./README.md) · 繁體中文（本頁）

依專案脈絡或引導式訪談，產出符合 [Google Stitch DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) 精神的完整設計系統文件與預覽資產。

## 什麼是 DESIGN.md？

[DESIGN.md](https://stitch.withgoogle.com/docs/design-md/overview/) 是以 **純 Markdown** 描述產品視覺與互動規則的設計系統文件，讓 AI 編碼代理或設計工具能一致地生成介面，無需 Figma 匯出或額外 schema。


| 檔案          | 誰讀取     | 定義內容       |
| ----------- | ------- | ---------- |
| `AGENTS.md` | 編碼代理    | 如何建置專案     |
| `DESIGN.md` | 設計／編碼代理 | 產品應有的外觀與體感 |


社群策展可參考 **[Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)**：從真實網站萃取、可直接複製的 `DESIGN.md` 與 `preview.html`／`preview-dark.html` 範本庫。  
**本倉庫**則提供 **「從零生成」** 的流程與章節模板（見 `[SKILL.md](./SKILL.md)`），適合自有產品、尚無現成 DESIGN.md 可抄的情境。

## 本倉庫內容


| 檔案                       | 說明                                                                                                      |
| ------------------------ | ------------------------------------------------------------------------------------------------------- |
| `[SKILL.md](./SKILL.md)` | **design-md-generator**：觸發條件、自主／引導雙模式、九章主模板、行動 App 擴充章節、反模式檢查清單，以及預設輸出的 **四件套**（`design-system/` 目錄）規格。 |


Skill 會引導代理產出與 [Stitch DESIGN.md 格式](https://stitch.withgoogle.com/docs/design-md/format/) 對齊的章節，並可延伸微互動預覽、明暗雙預覽等（細節以 `SKILL.md` 為準）。

## 使用方式

1. 將本倉庫的 `SKILL.md` 依 Cursor 的 [Agent Skills](https://docs.cursor.com) 方式安裝或引用（路徑依你的技能目錄設定而定）。
2. 在對話中使用觸發語，例如：**「生成 DESIGN.md」**、**「幫我做設計系統文件」**、**「產品視覺規範」** 等（完整列表見 `SKILL.md` 前端的 `triggers`）。
3. 選擇 **自主模式**（分析現有 README、樣式檔、技術棧）或 **引導模式**（逐步訪談產品氣質與限制）。
4. 依 Skill 預設，於專案的 `design-system/`（或你指定的根目錄）取得 `DESIGN.md`、`README.md`（品牌向簡介）、`preview.html`、`preview-dark.html` 等產出。

若你希望介面風格接近某個已公開的 DESIGN.md，可先從 [awesome-design-md 列表](https://github.com/VoltAgent/awesome-design-md) 挑選參考，再請代理在生成時對齊該風格或合併你的產品需求。

## 與 awesome-design-md 的分工


|     | [awesome-design-md](https://github.com/VoltAgent/awesome-design-md) | **本專案（design-md-generator）** |
| --- | ------------------------------------------------------------------- | ---------------------------- |
| 定位  | 策展現成 DESIGN.md + 預覽 HTML                                            | 定義「如何從頭寫一組」的代理流程與模板          |
| 適用  | 快速對齊知名產品視覺語言                                                        | 自有品牌、需訪談與反模板化（避免「AI 味」預設）    |


兩者都服務同一個目標：**讓 `DESIGN.md` 成為代理可讀、可執行的單一真相來源。**

## 延伸資源

- [Stitch：DESIGN.md 概覽](https://stitch.withgoogle.com/docs/design-md/overview/)
- [Stitch：DESIGN.md 格式說明](https://stitch.withgoogle.com/docs/design-md/format/)
- [VoltAgent／Awesome DESIGN.md](https://github.com/VoltAgent/awesome-design-md)
- [自訂 DESIGN.md 請求（getdesign.md）](https://getdesign.md/request)

## 授權

本倉庫以 [MIT License](./LICENSE) 授權。使用社群範本或第三方 `DESIGN.md` 時，請遵守各來源條款。