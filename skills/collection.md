# Skills 推薦收藏

記錄值得安裝的 Claude Code Skills，快速翻閱用。

- [萬用開發方法論](#萬用開發方法論)
- [規劃 / 任務管理](#規劃--任務管理)
- [前端 UI 設計](#前端-ui-設計)
- [生成圖表與圖解](#生成圖表與圖解)

---

## 萬用開發方法論

### Superpowers
**連結：** https://github.com/obra/superpowers

一套完整的 AI 輔助開發工作流，讓 Claude 更有條理地從需求走到上線。核心是**六階段流程**：

1. **Design** — 先問清楚需求，釐清模糊地帶
2. **Planning** — 拆成小任務，避免大爆炸式實作
3. **Implementation** — 用 subagent 驅動開發，含兩輪 code review
4. **Testing** — 強制 TDD，先寫測試再寫實作（RED-GREEN-REFACTOR）
5. **Review** — 自動化 code review 關卡
6. **Completion** — 處理 PR 與 merge 流程

**常被提到的亮點：** 頭腦風暴（brainstorm）功能，開始動工前先做結構化構思，適合需求不清晰或想探索多種方向時用。

支援 Claude Code、Cursor、GitHub Copilot、Gemini CLI、OpenAI Codex。

---

## 規劃 / 任務管理

### planning-with-files
**連結：** https://github.com/othmanadi/planning-with-files

靈感來自 Manus AI 的 context engineering，核心概念是**用三個持久化 markdown 檔案對抗 AI 記憶易失的問題**：

- `task_plan.md` — 追蹤整體計畫與各階段進度
- `findings.md` — 存放研究結果與重要發現
- `progress.md` — 每次工作階段的執行紀錄

跨 session 工作時 Claude 不會「忘記」前面做了什麼，特別適合多天才能完成的大型任務。官方測試數據：30 項指標通過率 96.7%、A/B 盲測 100% 勝出。

有人分享：先討論、規劃，再進入實作，Claude 會高度跟隨前期討論的計畫走，不容易在實作過程中自己偏掉。大專案或想先思考清楚再動手的情境非常推薦。

支援 17+ 平台：Claude Code、Cursor、GitHub Copilot、Gemini CLI、Codex 等，也有多語言版本（含繁中）。

---

## 前端 UI 設計

### 1. frontend-design（Anthropic 官方）
**連結：** https://github.com/anthropics/claude-code/blob/main/plugins/frontend-design/skills/frontend-design/SKILL.md

Anthropic 官方出品，目標只有一個：**讓 Claude 做出有個性的設計，而不是千篇一律的 AI 通用感**。Skill 裡明確列出了一堆禁忌，例如不准用 Inter 字體、不准用藍/灰配色、不准對稱置中佈局。

設計方向強調：
- **排版：** 選有個性的字體，大膽用比例與粗細對比
- **色彩：** 用 CSS 變數建立有凝聚力的配色系統
- **動畫：** 有劇本的動態，而不是隨便加 transition
- **空間：** 刻意的不對稱與留白

輸出支援 HTML/CSS/JS、React、Vue，產出可直接上線的程式碼。

### 2. ui-ux-pro-max-skill
**連結：** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill

龐大的 AI 設計規則庫，核心是一個有**推理引擎的設計系統產生器（v2.0）**。你描述你的專案需求，它分析後自動配出最適合的設計系統。

資料庫規模：
- 67 種 UI 風格（Glassmorphism、Claymorphism、Minimalism、AI-Native UI…）
- 161 組配色，依產品類型分類
- 57 種 Google Fonts 字型搭配
- 25 種圖表風格建議

四步流程：分析需求 → 多領域平行搜尋 → 推理引擎選配 → 輸出完整設計系統。

支援 React、Next.js、Vue、Angular、Laravel、SwiftUI、Flutter、HTML/Tailwind 等 15+ 技術棧。

### 3. Remotion Skills
**連結：** https://github.com/remotion-dev/remotion/tree/main/packages/skills/skills/remotion

Remotion 官方提供的 Claude Code skill，用 React 程式化生成影片時的最佳實踐指引。內容非常完整，有 30+ 個 rules 檔，涵蓋：

- 動畫、轉場、時間軸排序
- 音訊、字幕、靜音偵測
- 圖表、3D（Three.js）、Lottie
- 字型、圖片、影片嵌入
- FFmpeg 操作、AI 配音（ElevenLabs）

**適合：** 已在用 Remotion 做影片，或想結合網頁設計輸出動態影片內容。

---

## 前端設計到底要裝哪幾個？

| 需求 | 建議組合 |
|------|---------|
| 純前端介面 / 網頁設計 | `frontend-design` + `ui-ux-pro-max-skill` |
| 需要輸出動態影片 | 加裝 Remotion Skills |

`frontend-design` 負責**美感方向和設計思維**，`ui-ux-pro-max-skill` 負責**系統性的元件與配色規則庫**，兩者互補。

---

## 生成圖表與圖解

### lieflat-charts
**連結：** https://github.com/larashero3-dotcom/lieflat-charts

模板驅動的生成資料視覺化 skill，強調每張圖都要站得住腳。

- **有範本：** 60+ 張真實圖型庫，不會亂畫
- **有底線：** 禁止斷軸、發光、3D 等失真手法
- **能做報告：** 12 套中英文整頁模板

### eli5
**連結：** https://github.com/anthropics/claude-plugins-community/tree/main/eli5

`/eli5 <主題>`，一秒生成一張**大圖示、少文字**的解釋卡；取向跟 lieflat-charts 完全相反，**求快不求準**。

- **零門檻：** 裝完直接用，不用設定
- **零範本：** 畫法全靠 Claude 臨場發揮，最隨性
- **不一定好看：** 生成的圖不保證美觀，重點是講得懂

**兩者什麼情境該配合著用 → [eli5 × lieflat-charts：兩個 skill 怎麼配合](eli5-lieflat-charts.md)**
