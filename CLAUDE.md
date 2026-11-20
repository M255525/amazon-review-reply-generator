# amazon-review-reply-generator — Amazon 客評／客訴回覆信產生器

單檔前端工具（`index.html`＋`manual.html`），2026-09-20 建立。6 種情境（負評、正評、退貨、A-to-z 申訴、買家提問、物流客訴）套規則式範本，或選用 BYOK AI（Claude／OpenAI／Gemini／OpenRouter）產生英中對照的回覆信。

## 設計重點
- **規則式合規檢查**：偵測「以優惠換評論」等違反 Amazon 政策的用語；AI 產生的內容也會再跑一次檢查，不直接信任 AI。
- 6 組虛構範例，不含真實買家資料。
- RWD（<600px）：並排欄位改堆疊、觸控熱區加大、input／select／textarea 字級 16px 避免 iOS 自動縮放。
- Gemini 呼叫已套 `geminiModelFix()`（2026-11-09）。

## 序號授權（2026-09-21 使用者要求加上）
- 全螢幕 `#licenseGate`，骨架比照 `amazon-ppc-advisor`（主題色改琥珀 `--amber`），localStorage key `arrgLicenseSerial`。
- 後端沿用共用試算表「**跨境電商產品標題**」（`product-title-generator`／`amazon-listing-generator` 也在用），獨立分頁「AmazonReview序號」。和「跨境電商工具」試算表名稱相近，容易搞混。
- `clasp create --parentId` 會重置 `appsscript.json`，推送前改回 `Asia/Taipei`＋`USER_DEPLOYING`／`ANYONE_ANONYMOUS`。

## 部署
公開 repo，GitHub Actions 部署 Pages：<https://m255525.github.io/amazon-review-reply-generator/>。push 到 master 自動部署。

## 標準配備
跑馬燈（滑鼠移入暫停）、`manual.html`、使用警語、PWA（SW 只刪自己前綴的快取）、訪客計數器、創作者資訊。

## 驗證
無自動化測試。RWD 測試時 claude-in-chrome 視窗無法 resize，改用「本機靜態伺服器＋固定寬度 iframe」驗證 media query。改動後用工具健康檢查重查。
