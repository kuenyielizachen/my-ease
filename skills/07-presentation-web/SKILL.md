---
name: antigravity-presentation-web
description: 質感天空藍 Glassmorphism 簡報網站製作與部署指引。當使用者說要「製作簡報網站」「美化簡報」「部署簡報」時載入。
---

# 質感天空藍 Glassmorphism 簡報網站製作與部署指引

本 Skill 旨在完整記錄並重現一套**頂級珍珠白玻璃擬物（Pearl White Glassmorphism）與天空藍（Sky Blue）主調的 70 頁簡報網頁**製作、高階排版、雙向跳轉聯動、EMOJI 鮮豔彩色還原技術，以及自動化 GitHub Pages 部署流程。

## 🎨 一、 核心視覺與設計系統

在亮色（Light Theme）的天空藍色調中，必須維持高對比與空氣質感：

### 1. CSS 配色變數 (`:root`)
```css
:root {
  --bg-dark: #f0f9ff;          /* 晴空淺藍 */
  --bg-slate: #e0f2fe;         /* 柔軟雲朵藍 */
  --primary: #0284c7;          /* 天空藍主色 */
  --primary-glow: rgba(14, 165, 233, 0.18);
  --secondary: #0d9488;        /* 深海綠 (次要色) */
  --secondary-glow: rgba(13, 148, 136, 0.18);
  --accent: #e11d48;           /* 玫瑰紅 (強烈對比色) */
  --text-main: #0f172a;        /* 石板深灰 (高對比主字體) */
  --text-muted: #475569;       /* 灰藍色 (說明性文字) */
  --glass-bg: rgba(255, 255, 255, 0.78); /* 高透光度珍珠玻璃 */
  --glass-border: rgba(14, 165, 233, 0.16); /* 天空藍微光邊框 */
}
```

### 2. 環境飄逸背景
* **圓形流光動畫**：使用 `glow-1` 與 `glow-2` 兩個大圓形（`38bdf8` 與 `22d3ee`），設定 `0.45` 的高不透明度與模糊濾鏡（`filter: blur(120px)`），打造風和日麗的晴空質感。

### 3. 標題漸層與 EMOJI 彩色原生還原技術 (🔥 極其重要)
* **漸層文字剪裁**：標題使用從石板深灰到天空藍的線性漸層：`linear-gradient(to right, #0f172a, #334155)`。
* **EMOJI 單色遮罩問題**：當標題使用 `-webkit-background-clip: text` 與 `-webkit-text-fill-color: transparent` 時，內部放置的 EMOJI 會被瀏覽器當成透明字體裁剪，丟失色彩呈現黑白。
* **還原方案**：必須將標題中的 EMOJI 包裝在 `<span class="emoji-color">` 中，利用 CSS 覆蓋重置，徹底解放 EMOJI 的彩度：
```css
.emoji-color {
  background: none !important;
  -webkit-background-clip: initial !important;
  background-clip: initial !important;
  -webkit-text-fill-color: initial !important;
  text-fill-color: initial !important;
  color: initial !important;
  display: inline-block;
  vertical-align: middle;
  font-family: "Segoe UI Emoji", "Apple Color Emoji", "Noto Color Emoji", "Segoe UI Symbol", sans-serif;
  margin-left: 0.35rem;
}
```

---

## 🛠️ 二、 高階排版佈局結構

### 1. 首頁 3D 立體實體書本 Split 佈局
將首頁改為左文右圖佈局，右側採用高逼真的 3D 書本展示：
```html
<div class="slide-card split">
  <div class="slide-left" style="align-items: flex-start; text-align: left; padding-right: 0;">
    <!-- 封面文案 -->
  </div>
  <div class="slide-right" style="display: flex; align-items: center; justify-content: center; height: 100%;">
    <div class="cover-image-container">
      <div class="book-3d">
        <img src="book-cover.jpg" alt="書籍封面">
      </div>
    </div>
  </div>
</div>
```
* **3D 書籍 CSS 特效**：
```css
.cover-image-container {
  display: flex;
  align-items: center;
  justify-content: center;
  width: 100%;
  height: 100%;
  perspective: 1200px;
}
.book-3d {
  width: 260px;
  height: 370px;
  position: relative;
  transform: rotateY(-16deg) rotateX(8deg) rotateZ(-2deg);
  transform-style: preserve-3d;
  box-shadow: -15px 15px 30px rgba(15, 23, 42, 0.15);
  transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1), box-shadow 0.6s cubic-bezier(0.16, 1, 0.3, 1);
  border-radius: 4px 14px 14px 4px;
}
.book-3d:hover {
  transform: rotateY(-4deg) rotateX(4deg) rotateZ(0deg) scale(1.04);
  box-shadow: -25px 25px 45px rgba(15, 23, 42, 0.22);
}
.book-3d::before {
  content: '';
  position: absolute;
  top: 0; left: 0; width: 12px; height: 100%;
  background: linear-gradient(to right, rgba(15,23,42,0.2) 0%, rgba(255,255,255,0.15) 30%, rgba(15,23,42,0.05) 100%);
  border-radius: 4px 0 0 4px;
  z-index: 5;
}
```

### 2. 才德上品/毒品矩陣 (Slide 17)
採用 4 格 Grid 佈局（`character-matrix`），為每個單元添加 `🌟`、`🤝`、`☠️`、`🍂` EMOJI 作為視覺引導。

### 3. 多功能列表佈局 (Slide 39)
為 `feature-item` 配置 `<div class="feature-icon">`，包含 `💰`、`🛡️`、`🙇‍♂️`、`🌱` EMOJI，保持與其他投影片的視覺一致。

---

## ⚡ 三、 交互功能：雙向分組過濾與跳轉同步

### 1. 頁籤分組 (Part Tabs)
將 70 頁簡報細分為 5 個 Part：
```html
<div class="part-tabs">
  <button class="part-tab active" data-part="all">全部</button>
  <button class="part-tab" data-part="part1">開顯生命 (01-17)</button>
  <button class="part-tab" data-part="part2">了凡改命 (18-41)</button>
  <button class="part-tab" data-part="part3">品格美學 (42-49)</button>
  <button class="part-tab" data-part="part4">讀者回響 (50-69)</button>
  <button class="part-tab" data-part="part5">結語 (70)</button>
</div>
```

### 2. 點擊頁籤：Drawer 過濾與直接跳轉
點擊頂部 Tab，過濾左側目錄，並立刻**直接跳轉**至該大單元的第一頁：
```javascript
let jumpIndex = -1;
if (part === 'part1') jumpIndex = 0;
else if (part === 'part2') jumpIndex = 17;
else if (part === 'part3') jumpIndex = 41;
else if (part === 'part4') jumpIndex = 49;
else if (part === 'part5') jumpIndex = 69;

if (jumpIndex !== -1) goToSlide(jumpIndex);
```

### 3. 滑動/鍵盤切換：反向高亮同步
當使用者按下左右方向鍵或 Space 切換投影片時，在 `updateSlideClasses()` 內部，自動根據當前的 `currentSlide` 索引，精準匹配並點亮對應的頂部頁籤與左側抽屜目錄項。

### 4. 靜態骨架防閃爍
為防止 JavaScript 執行前的「頁數與標題不對稱閃爍」，HTML 骨架中寫死的文字必須與 JS 加載後一致（即寫死為 `Slide 1 / 70` 與 `全書 70 節目錄`）。

---

## 🚀 四、 發佈與部署工作流程

1. **雙向拷貝同步**：
   將修改後的專案根目錄 `index.html` 完美拷貝覆蓋至 `presentation/index.html`，保證兩處版本完全同步：
   ```powershell
   Copy-Item -Path "index.html" -Destination "presentation\index.html" -Force
   ```
2. **圖片資源的 Git 繞過強制上傳**：
   由於專案的 `.gitignore` 預設忽視了 `*.jpg`、`*.png` 等所有圖像格式，若直接 commit 會遺失封面相片。必須使用 `-f` 強制加入：
   ```powershell
   git add -f book-cover.jpg presentation/book-cover.jpg
   ```
3. **安全提交與推送**：
   ```powershell
   git add index.html presentation/index.html
   git commit -m "style: 簡報網頁視覺更新與功能優化"
   git push origin main
   ```
4. **驗證線上 Pages**：訪問 `https://<username>.github.io/<repo-name>/` 進行部署確認。
