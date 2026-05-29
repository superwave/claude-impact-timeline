# Anthropic 動態追蹤 (Claude Impact Tracker)

單一檔案的靜態網頁，追蹤 2026 年 Anthropic / Claude 的重大動態（模型發佈、合作、市場衝擊、募資、治理）。
部署在 GitHub Pages：<https://superwave.github.io/claude-impact-timeline/>

## 架構（重點）

- **整個網站就是 `index.html` 一個檔案**（HTML + CSS + JS 全內嵌），沒有 build step、沒有相依套件安裝。Chart.js 由 CDN 載入。
- **資料驅動**：頁面內容由 `<script>` 裡的 `const DATA = {...}` 自動渲染。
  - `DATA.events[]` — 所有事件。**最新動態** feed（按月、最新在上）與 **故事線**（按 phase）都讀同一份。
  - `DATA.phases[]` — 故事線的分期（`{name, sub}`）。
- 分頁 UX：`📰最新動態 / 📖故事線 / 🏭產業動向 / 📈股價 / 🔮預測`，由 `showTab()` 切換。股價 Chart.js 圖在切到該分頁時才 lazy 初始化。

## 如何新增一則事件（最常見的更新）

**只要在 `DATA.events` 陣列裡加一個物件即可** — feed 和故事線會同時自動出現。

```js
{
  id: '',                              // 選填，給錨點用；沒有就空字串
  dot: 'partner',                      // 視覺顏色：anthropic-official|release(橘) / partner(藍) / impact(紅) / recovery(綠)
  date: '2026-06-15',                  // ISO，排序用（必填）
  dateLabel: '2026 年 6 月 15 日',      // 顯示用日期字串（可含「— 事件名」後綴）
  official: true,                      // 是否官方來源（顯示「Anthropic 官方」badge）
  titleHtml: '事件標題',                // 可含 <strong> 等
  desc: '整理過的敘述，可含 <strong>、<br>、<a>',
  sources: [ {label:'Anthropic 官方', url:'https://...'}, {label:'CNBC', url:'https://...'} ],
  phase: 'Phase 7 — 登頂時刻：逼近 $1 兆估值（2026.05 下旬）',  // 選填，見下方
  type: 'fund'                         // 選填，見下方
}
```

### 自動處理的部分（不必擔心）
- **`type` 可省略** — 載入時依 `id`／標題關鍵字／`dot` 自動推導，並有預設後備。手動指定時用：`model`(模型・產品) / `partner`(合作・收購) / `impact`(市場衝擊) / `fund`(募資・估值) / `gov`(治理・政策)。
- **順序不必管** — 載入時自動依 `date` 排序，亂序插入也沒事。
- **`phase` 可省略或對不到** — 故事線會把這類事件自動收進「其他 / 未分期」區，**不會消失**。要精準歸到某段故事，`phase` 必須**完全等於** `DATA.phases` 裡某個 `name`。
- **「追蹤 N 則」計數自動更新**（讀 `DATA.events.length`）。

### ⚠️ 注意：`DATA` 是壓縮成一行的 JSON
`const DATA={...}` 是單行 minified JSON（約 100KB），不適合人工手改。新增時：在該行的 `"events":[ ... ]` 陣列**結尾**（最後一個事件物件之後）插入新物件即可。用編輯工具精準插入，別動到其他部分。

## 開新分期（Phase）
若事件屬於新階段（例如 Phase 8），在 `DATA.phases` 陣列尾端加：
```js
{ name:'Phase 8 — 標題（2026.06）', sub:'這一階段的一句話摘要' }
```
然後把該階段事件的 `phase` 設成完全相同的 `name`。故事線會依 `DATA.phases` 的順序顯示。

## 更新股價圖（次要，已非追蹤重點）
股價資料在 `drawStockChart()` 函式內的 `const stocks = [...]`，每支股票有 `keys: [['YYYY-MM-DD', 指數值], ...]`（100 = 2026/1/1 基準）。延長走勢就往各股 `keys` 尾端加資料點，並更新 x 軸 `max:` 與圖上的事件註記 `annotations`。
> 股價為「公開報導百分比估算」，非即時數據，頁面已標明不構成投資建議——維持此免責聲明。

## 每次更新別忘了改的手動欄位
- 頂部 `最後更新 2026/MM/DD`（`index.html` 搜尋 `最後更新`）。
- 頂部估值 chip `估值 $9,650 億`（若有新一輪募資/估值）。
- （選用）`預測`分頁頂部的「✅ 已實現」狀態列，若某預測成真。

## 驗證
- JS 語法：把最後一個 `<script>` 內容存檔後 `node --check`。
- 實際渲染：用瀏覽器開 `file://.../index.html`，或 Chrome DevTools MCP 載入後檢查 console 無錯、切換各分頁、點篩選 chips。

## 部署
GitHub Pages 設定為 `main` 分支根目錄，**push 到 `main` 即自動部署**：
```bash
git add index.html && git commit -m "..." && git push origin main
```
查部署狀態：`gh api repos/superwave/claude-impact-timeline/pages/builds/latest`。約 1–2 分鐘生效。

## Commit 慣例
訊息用繁體中文。結尾署名：
```
Co-Authored-By: Claude Opus 4.8 (1M context) <noreply@anthropic.com>
```
