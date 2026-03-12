# Anthropic 衝擊波時間軸（The Claude Effect Timeline）

## 專案概述

這是一份互動式 HTML 時間軸報告，記錄 Anthropic 每次重大產品發佈如何引發相關產業的股價震盪。從 2025 年初的技術累積期到 2026 年的全面衝擊，涵蓋了 **8 個產業別**的市場反應。

核心觀察：Anthropic 的產品釋出節奏與特定產業的股價下跌呈現高度時間相關性，媒體已正式稱之為「The Claude Effect」。

## 檔案結構

```
claude-impact-timeline/
├── anthropic-impact-timeline.html   ← 唯一的產出檔（自包含，無外部依賴）
├── README.md                        ← 本檔案
└── .claude/                         ← Claude 專案設定
```

## 技術架構

單一 HTML 檔案，約 985 行，包含所有 CSS 和 JavaScript。唯一的外部資源是 Google Fonts（Inter + Noto Sans TC）。

### 視覺設計
- 深色主題（`#0a0a0f` 背景）
- 事件圓點顏色系統：🟠 橘色 = 產品發佈、🔴 紅色 = 市場衝擊、🔵 藍色 = 合作夥伴、🟢 綠色 = 市場回穩
- 所有金額統一使用 `USD $` 前綴

### 互動功能
- **固定導航列**：頂部 sticky nav，點擊跳轉各 Phase
- **Phase 標籤黏著效果**：每個 Phase 標題在滾動時會固定在 `top: 44px`（nav 高度下方），使用 `IntersectionObserver` + sentinel div 偵測黏著狀態並加上發光效果
- **滾動導航高亮**：當前可見的 Phase 在 nav 中自動高亮
- **響應式設計**：768px 斷點

## 目前涵蓋的內容

### 時間軸 Phases

| Phase | 名稱 | 時間 | 重點事件 |
|-------|------|------|----------|
| Phase 0 | 技術累積期 | 2025 Q1-Q3 | Claude 3.5 Sonnet、Claude Code、Model Context Protocol、Computer Use |
| Phase 1 | Cowork & Plugins 生態啟動 | 2025 Q4 – 2026/1 | Cowork 發佈、Legal Plugin、法律科技股崩盤 |
| Phase 2 | Opus 4.6 與 SaaSocalypse | 2026/2 上旬 | Opus 4.6 發佈、SaaS 崩盤、金融數據股衝擊、印度 IT 股崩盤 |
| Phase 3 | 資安攻防 | 2026/2/20 | Claude Code Security 發佈、資安股下跌 |
| Phase 4 | Legacy 清算 | 2026/2/23 | COBOL 遷移宣言、IBM 股價暴跌、The Great Stabilization |
| Phase 5 | 下一波預告 | 2026/3 | 旅遊業警告（Skift 報導）、Microsoft Copilot Cowork 回應 |

### 產業衝擊卡片（8 個）

1. **Legal Tech** — Thomson Reuters、LexisNexis 等
2. **SaaS** — ServiceNow、Salesforce、Workday 等
3. **Indian IT** — TCS、Infosys、Wipro（Nifty IT）
4. **Cybersecurity** — CrowdStrike、Okta、Palo Alto
5. **Financial Data** — FactSet、Morningstar、S&P Global
6. **Legacy Systems / IT Consulting** — IBM、Accenture、DXC
7. **Healthcare**（觀察中）— 尚未出現明顯股價衝擊
8. **Travel**（預警中）— Skift 報導指出旅遊業可能是下一波

### 衝擊幅度長條圖

14 條數據，每條包含：代表性個股、最大跌幅百分比、時間範圍註記。

## 如何新增事件

### 新增一個時間軸事件

在對應的 Phase section 內加入以下 HTML 結構：

```html
<div class="event" id="可選的錨點ID">
  <div class="dot [release|impact|partner|recovery]"></div>
  <div class="event-content">
    <div class="event-date">YYYY/MM/DD</div>
    <h3>事件標題</h3>
    <p>事件描述。<a href="來源URL" target="_blank">來源名稱</a></p>
    <!-- 如果是衝擊事件，加入數據標籤 -->
    <div class="tags">
      <span class="tag impact">個股 -X%</span>
      <span class="tag impact">指數 -Y%</span>
    </div>
  </div>
</div>
```

dot class 對應：
- `release` → 橘色（Anthropic 產品發佈）
- `impact` → 紅色（市場衝擊）
- `partner` → 藍色（合作或競爭回應）
- `recovery` → 綠色（市場回穩）

### 新增一個 Phase

1. 在 nav `.toc` 中加一個連結：`<a href="#phaseX">Phase X</a>`
2. 在時間軸中加入新的 phase-label 區塊（需含 sentinel div，JS 會自動偵測）
3. Phase label HTML：

```html
<div class="phase-sentinel"></div>
<div class="phase-label" id="phaseX">
  <h2>Phase X — 標題</h2>
  <p>副標題描述</p>
</div>
```

### 新增產業卡片

在 `.sector-grid` 區域加入：

```html
<div class="sector-card">
  <h3>🔥 產業名稱</h3>
  <p>產業衝擊摘要。</p>
  <div class="tags"><span class="tag impact">代表性指標</span></div>
</div>
```

### 新增長條圖條目

在 bar chart section 的 `.chart` div 內加入：

```html
<div class="bar-row">
  <div class="bar-label">日期標記 · 個股名稱 · 時間範圍</div>
  <div class="bar-track">
    <div class="bar impact" style="width: XX%;">-XX%</div>
  </div>
</div>
```

`width` 比例：以目前最大跌幅（Nifty IT -19%）為 95% 基準，按比例計算。

## 資料來源與查證

所有數據都應有新聞來源佐證。主要參考來源：

- **Bloomberg** — 個股與指數即時數據
- **CNBC** — 市場反應分析
- **Fortune** — 產業趨勢報導
- **Reuters** — 全球市場影響
- **Seeking Alpha** — 個股深度分析
- **Skift** — 旅遊產業專題
- **Indian financial media**（Economic Times、Moneycontrol）— 印度 IT 股數據

查證新事件時，建議搜尋：`"Claude" OR "Anthropic" stock crash site:bloomberg.com OR site:cnbc.com`

## 未來更新方向

以下是已知需要追蹤的事件與產業：

- [ ] **Claude 5 發佈**：預期將引發新一輪衝擊
- [ ] **旅遊產業實際衝擊**：Skift 已發出預警，追蹤 Booking、Expedia、Sabre 等股價
- [ ] **Healthcare 衝擊落地**：Claude for Healthcare 已在 JPM Conference 亮相，追蹤 Epic、Veeva、Teladoc
- [ ] **教育產業**：Chegg 已受 AI 衝擊，追蹤是否有 Claude 特定事件
- [ ] **會計/審計**：四大會計師事務所相關上市公司反應
- [ ] **The Great Stabilization 後續**：市場是否真正回穩，或只是暫時性反彈
- [ ] **更新 hero 區統計數字**：目前顯示 7 產業、USD $285B+ 蒸發、4 個月（隨新事件更新）

## 注意事項

- 這份報告記錄的是「時間相關性」而非「因果關係」— 股價下跌可能有多重因素
- 所有股價數據以事件發生時的報導為準，後續可能有修正
- HTML 檔案是自包含的，可以直接用瀏覽器開啟，不需要任何 server
- 修改後建議在瀏覽器中檢查 sticky 效果和 nav 高亮是否正常運作
