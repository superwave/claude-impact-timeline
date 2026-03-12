# Stock Impact Data — Anthropic Timeline

## Company Reference

| Stock | Ticker | Yahoo Finance URL | Description (zh-TW) |
|-------|--------|-------------------|---------------------|
| IBM | IBM | https://finance.yahoo.com/quote/IBM | 全球大型主機與遺留系統服務商，COBOL 維護年收入約 USD $200 億 |
| Coforge | COFORGE.NS | https://finance.yahoo.com/quote/COFORGE.NS | 印度 IT 服務商，專精數位轉型與現代化 |
| Infosys | INFY | https://finance.yahoo.com/quote/INFY | 印度第二大 IT 服務商，30 萬+員工，人力外包模式 |
| LegalZoom | LZ | https://finance.yahoo.com/quote/LZ | 線上法律文件準備與小企業成立服務平台 |
| Nifty IT | ^CNXIT | https://finance.yahoo.com/quote/%5ECNXIT | 印度國家證交所 IT 產業指數，涵蓋印度前 10 大 IT 公司 |
| CrowdStrike | CRWD | https://finance.yahoo.com/quote/CRWD | 端點偵測與回應 (EDR) 及威脅情報平台 |
| Thomson Reuters | TRI | https://finance.yahoo.com/quote/TRI | 全球法律、稅務、新聞內容與分析平台，擁有 Westlaw |
| Microsoft | MSFT | https://finance.yahoo.com/quote/MSFT | Office 365、Azure 雲端平台，全球最大軟體公司 |
| RELX | RELX | https://finance.yahoo.com/quote/RELX | 英國 FTSE 100 公司，擁有 LexisNexis 法律研究平台 |
| Okta | OKTA | https://finance.yahoo.com/quote/OKTA | 身份與存取管理 (IAM) 雲端平台 |
| FactSet | FDS | https://finance.yahoo.com/quote/FDS | 金融數據與分析終端供應商，Bloomberg 主要競爭對手 |
| SailPoint | SAIL | https://finance.yahoo.com/quote/SAIL | 身份安全與治理平台 |
| Morningstar | MORN | https://finance.yahoo.com/quote/MORN | 投資研究、評級與投資組合管理軟體 |

## Key Price Movements

### Thomson Reuters (TRI) — V-Shape Story
- Jan 1: Baseline 100
- Feb 3: -15.8% single day (Legal Plugin crash, historic worst day)
- Feb 6: ~-30% YTD (SaaSocalypse deepens)
- Feb 24: +11% (Relief Rally, CEO Steve Hasker at Anthropic event)
- The ultimate "enemy becomes partner" story

### IBM — Most Dramatic Single Event
- Feb 23: -13.2% single day (COBOL blog, $310B evaporated)
- Feb 25: +2.67% (Great Stabilization)
- Feb total: -27% (worst since 1968)

## Chart Data Points (Index 100 = Jan 1)

### Thomson Reuters (TRI)
```
Jan 1: 100 | Jan 5: 99.5 | Jan 10: 99 | Jan 12: 97 | Jan 15: 96
Jan 20: 95 | Jan 25: 93 | Jan 28: 92 | Jan 30: 90 | Feb 1: 88
Feb 3: 84.2 | Feb 4: 80 | Feb 5: 76 | Feb 6: 70 | Feb 10: 72
Feb 14: 71 | Feb 18: 72 | Feb 20: 71 | Feb 22: 70 | Feb 24: 77.7
Feb 25: 79 | Feb 27: 80 | Mar 1: 81 | Mar 3: 82 | Mar 5: 83
Mar 8: 84 | Mar 10: 84.5 | Mar 12: 85
```

### IBM
```
Jan 1: 100 | Jan 5: 99 | Jan 10: 98 | Jan 12: 96 | Jan 15: 95
Jan 20: 94 | Jan 25: 92 | Jan 28: 91 | Jan 30: 89 | Feb 1: 87
Feb 3: 84 | Feb 4: 82 | Feb 5: 80 | Feb 6: 78 | Feb 10: 77
Feb 14: 76 | Feb 18: 76 | Feb 20: 74 | Feb 22: 75 | Feb 23: 65.1
Feb 24: 66 | Feb 25: 67.8 | Feb 27: 70 | Mar 1: 72 | Mar 3: 73
Mar 5: 73.5 | Mar 8: 74 | Mar 10: 74 | Mar 12: 73
```

## Bar Chart Data (14 rows, sorted by magnitude)

| Rank | Sector | Stock | Decline | Period | Trigger |
|------|--------|-------|---------|--------|---------|
| 1 | 遺留系統 | IBM | -27% | 2月整月 | COBOL blog |
| 2 | 印度 IT | Coforge | -23% | 2月整月 | SaaSocalypse |
| 3 | 印度 IT | Infosys | -23% | 2月整月 | SaaSocalypse |
| 4 | 法律科技 | LegalZoom | -19.7% | 2/3 單日 | Legal Plugin |
| 5 | 印度 IT | Nifty IT | -19% | 2月整月 | India IT crash |
| 6 | 資安 | CrowdStrike | -17% | 4日 | Code Security |
| 7 | 法律科技 | Thomson Reuters | -15.8% | 2/3 單日 | Legal Plugin |
| 8 | SaaS | Microsoft | -14% | 1/30-3/9 | Cowork era |
| 9 | 法律科技 | RELX | -14% | 2/3 單日 | Legal Plugin |
| 10 | 遺留系統 | IBM | -13.2% | 2/23 單日 | COBOL blog |
| 11 | 資安 | Okta | -13% | 4日 | Code Security |
| 12 | 金融數據 | FactSet | -10.5% | 2/3-6 | Finance Plugin |
| 13 | 資安 | SailPoint | -9.4% | 2/20 單日 | Code Security |
| 14 | 金融數據 | Morningstar | -9% | 2/3-6 | Finance Plugin |

## Relief Rally (Feb 24) — Green Stocks
| Stock | Change | Trigger |
|-------|--------|---------|
| Thomson Reuters | +11% | CEO at Anthropic event |
| FactSet | +6% | Partnership signal |
| Salesforce | +4% | Slack integration |
| DocuSign | +2%+ | MCP connector |
| LegalZoom | +2%+ | Partnership pivot |
| IBM | +2.67% (Feb 25) | Amodei stabilization |
