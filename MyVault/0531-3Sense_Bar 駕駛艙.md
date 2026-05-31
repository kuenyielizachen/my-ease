# 0531-3Sense_Bar 專案駕駛艙

本專案由 AI 協作開發，旨在為您打造《從容而行：笑納人生的智慧》全書 50 章節深度導覽演示簡報，並整合了多個 MCP 服務模組（NotebookLM、Obsidian Vault、Google Workspace 等）。

## 🚀 專案現況與進度

- **互動演示網頁**：已完成位於 [presentation/index.html](file:///d:/Antigravity%20Works/0531-3Sense_Bar/presentation/index.html) 的客製化單頁式極緻美學簡報網頁。
- **簡報頁數**：已成功擴充至 **50 頁（包含封面、前言、三大單元 47 個詳細章節，以及結語）**。
- **視覺與特效**：
  - 極具質感的 **Glassmorphism（玻璃擬物）卡片佈局**。
  - **動態環境流光背景**（Radial Gradient 與微幅飄移 CSS 動態）。
  - **4 區分層過濾頁籤**（開顯生命 01-17、了凡改命 18-41、品格美學 42-49、結語 50）與全部視窗切換。
  - **動態左側目錄抽屜（Drawer Menu）**，可即時過濾並選取章節進行跳轉。
  - **鍵盤控制支援**（左/右方向鍵、Space 鍵）與 **行動端 Swipe（滑動）手勢支援**。
  - **底端進度條**與分頁進度同步更新。

---

## 🛠️ MCP 服務整合紀錄

1. **NotebookLM 連接**
   - 帳戶：`kuenyielizachen@gmail.com`
   - 目前已成功讀取並列出 43 個筆記本，並深入分析《從容而行》的核心脈絡。
2. **Obsidian Vault 連接**
   - 目前本機 Vault 路徑：[MyVault](file:///d:/Antigravity%20Works/0531-3Sense_Bar/MyVault)
   - 已透過 `@bitbonsai/mcpvault` 全自動化橋接，AI 可即時讀取並寫入本庫筆記。
3. **Google Workspace 連接**
   - OAuth 憑證：安全儲存於 `C:\Users\kuenyi\.google-workspace-mcp\credentials.json`
   - 授權權杖：`token.json` 已順利生成，打通 Google Drive 與 Calendar 的 MCP 存取權。
   - 經測試：已能成功獲取 Google 雲端硬碟的前 10 個文件清單。

---

## 🧭 全書 50 章節架構總覽

1. **封面與前言**
   - Slide 01: 從容而行 (封面)
   - Slide 02: 前言：功利時代心靈荒原
2. **單元一：開顯無盡藏 (01-17)**
   - Slide 03: 1.1 物欲與快樂隱形對立
   - Slide 04: 1.2 女性快樂指數 Paradox
   - Slide 05: 1.3 心靈指標之首：安心
   - Slide 06: 1.4 安心與功利社會危機
   - Slide 07: 1.5 憂鬱盛行率數據警示
   - Slide 08: 1.6 優秀學子自戕之警示
   - Slide 09: 1.7 什麼是主觀人生價值
   - Slide 10: 1.8 主觀價值之宿命脆弱
   - Slide 11: 1.9 什麼是客觀人生價值
   - Slide 12: 1.10 德蕾莎修女無私典範
   - Slide 13: 1.11 綱領一：助迷惑者覺醒
   - Slide 14: 1.12 綱領二：助苦難者解脫
   - Slide 15: 1.13 知識之本質：向外馳求
   - Slide 16: 1.14 智慧之本質：內省高明
   - Slide 17: 1.15 德者才之主與才德四象
3. **單元二：了凡改命 (18-40)**
   - Slide 18: 了凡四訓導讀與流傳歷史
   - Slide 19: 2.1.1 袁了凡幼年放棄科舉
   - Slide 20: 2.1.2 慈雲寺偶遇神相孔仙
   - Slide 21: 2.1.3 孔先生對命運鐵定預測
   - Slide 22: 2.1.4 棲霞山與雲谷禪師對坐
   - Slide 23: 2.1.5 雲谷禪師痛斥凡夫認命
   - Slide 24: 2.1.6 雲谷開示立命改造大理
   - Slide 25: 2.1.7 一切福田不離自心方寸
   - Slide 26: 2.2.1 改過：轉禍為福的起點
   - Slide 27: 2.2.2 改過三心之一：羞恥心
   - Slide 28: 2.2.3 改過三心之二：敬畏心
   - Slide 29: 2.2.4 改過三心之三：勇猛心
   - Slide 30: 2.2.5 事上改過之法 (治標)
   - Slide 31: 2.2.6 理上改過之法 (順理)
   - Slide 32: 2.2.7 心上改過之法 (最上乘)
   - Slide 33: 2.3.1 積善之方：明辨善惡真偽
   - Slide 34: 2.3.2 積善之方：明辨陰德陽善
   - Slide 35: 2.3.3 積善之方：明辨端曲半滿
   - Slide 36: 2.3.4 十大善行：與人為善 (帝舜)
   - Slide 37: 2.3.5 十大善行：愛敬存心 (仁禮)
   - Slide 38: 2.3.6 十大善行：成人之美與勸善
   - Slide 39: 2.3.7 十大善行：救人危急興建大利
   - Slide 40: 2.3.8 十大善行：捨財/護法/敬長/愛物
   - Slide 41: 2.4 謙德之效：易經第一吉卦謙卦
4. **單元三：品格美學與結語 (42-50)**
   - Slide 42: 3.1 五階段品格智慧教育前言
   - Slide 43: 3.2 幼兒養性 (0-3歲奠基)
   - Slide 44: 3.3 童蒙養正 (4-13歲經典)
   - Slide 45: 3.4 少年養志 (13歲後立志)
   - Slide 46: 3.5 成年養德 (職場修身)
   - Slide 47: 3.6 晚年養道 (傳承與笑納)
   - Slide 48: 3.7 實踐門徑：奉行忠與恕
   - Slide 49: 3.8 極致內省：不遷怒不貳過
   - Slide 50: 3.9 讀者迴響與行深見證 / 結語

---

## 📝 開發筆記與踩坑紀錄

1. **PowerShell 指令環境限制**
   - 由於 Windows PowerShell 預設限制 `.ps1` 腳本執行，若要在終端環境下執行 `npm` / `npx` 指令，請使用 `npm.cmd` 與 `npx.cmd` 作為指令前置名稱。
2. **Windows 命令行逸出字元 (Caret Escape) 陷阱**
   - 在 CMD/PowerShell 調用瀏覽器開啟 URL 時，若使用了 `.replace(/&/g, '^&')` 來做 caret escape 並同時用雙引號包覆 URL，可能會導致瀏覽器收到的 URL 多出 `^` 逸出字元（進而導致 Google 驗證出現 Error 400）。直接傳遞完整的雙引號 URL 即可避免此一問題。
3. **Google API 測試使用者權限限制**
   - Google Cloud Console 專案處於 Testing（測試中）階段且涉及 sensitive scope 時，必須在 OAuth 同意畫面的「Test Users」手動新增 `kuenyielizachen@gmail.com`，否則即使是專案建立者也會遇到 `Error 403: access_denied` 封鎖。

---

*本文件作為 Obsidian 駕駛艙筆記保存，當您使用 Obsidian 開啟本 Vault 時，即可無縫瀏覽此項進度與指引。*
