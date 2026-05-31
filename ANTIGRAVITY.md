# 0531-3Sense_Bar - ANTIGRAVITY.md

## 專案入口

專案名稱：0531-3Sense_Bar
專案用途：Anti-Gravity 懶人包整合與工作空間
主要工作目錄：d:\Antigravity Works\0531-3Sense_Bar
GitHub repo：https://github.com/mathruffian-dot/antigravity-lazy-pack
預設 branch：main

## Obsidian 對應筆記

Obsidian vault：d:\Antigravity Works\0531-3Sense_Bar\MyVault
專案駕駛艙：MyVault\Welcome.md (或在此建立 0531-3Sense_Bar 駕駛艙.md)

## 工作規則

- 回應使用繁體中文（Taiwan）。
- 涉及檔案操作時回報完整產出位置與絕對路徑。
- 使用 Windows PowerShell 語法來執行所有終端指令。
- **開工流程**：讀取本檔 `ANTIGRAVITY.md`、讀取 Obsidian 專案駕駛艙、執行 `git status` 與最近變更檢查。
- **收工流程**：更新 Obsidian 專案駕駛艙（踩坑、進度），唯有固定規則變動時才更新本檔，檢查 `git diff` 與 `git status`，杜絕無差別 `git add .`，只提交與本次任務相關的乾淨檔案。
- 不把每日流水帳或暫存產物寫入本檔。

## 生圖與媒體規則 (04-draw)

- **內建生圖優先**：直接使用自然語言進行生圖，不把 `OPENAI_API_KEY` 提交或寫入任何專案檔案。
- **提示詞結構**：
  ```text
  生成一張圖片：
  用途：
  尺寸比例：
  主題：
  畫面內容：
  風格：
  色彩：
  文字：
  限制：
  輸出位置：
  ```
- **路徑限制**：生成之專案圖片放置於 `assets/` 或 Obsidian 附件資料夾，切勿將臨時產物直接提交至 Git。

## 不要做

- **❌ 嚴禁提交敏感資料**：包含 API key、GitHub token、Firebase Admin 私鑰憑證。
- **❌ 嚴禁提交 NotebookLM 私人匯出檔**：包括 `notebooks.json` 或筆記本 ID 清單。
- **❌ 嚴禁進行無差別 Git 提交**：務必仔細審查 `git status` 與 `git diff`。
- **❌ 嚴禁儲存真實個人隱私**：若涉及學生資料，僅可使用班級代號與座號，不儲存真名。
