# Claude Code Collection

由 CYouuu 整理，收錄 Claude Code 相關的自製功能、插件設定與 Skills 推薦。

不定期更新，內容以實際使用過、覺得有價值的為主，而不是大量堆積。

---

## 內容

### Hooks — macOS 提醒通知

#### [Claude Code 版](hooks/macos-notification.md)

自製的兩個 hooks，偵測使用者是否正在看著 Claude Code：

- 需要授權時發出提示音與通知
- 完成時發出靜音通知

適合常常讓 Claude 在背景執行任務、自己切去其他視窗或軟體工作的情境。

#### [Codex 版](hooks/codex-macos-notification.md)

移植到 Codex 的 macOS hooks 設定：

- 權限請求時發出提示音與通知
- 完成時發出靜音通知

Codex 的 `PermissionRequest` 會在權限 UI 顯示前觸發，所以提示音會比畫面上的權限詢問更早出現。

---

### [插件 — claude-hud 狀態列](plugins/claude-hud.md)

在終端機下方顯示常駐狀態列，即時呈現模型、Context 用量、Token 費用、Agent 狀態、Git 分支等資訊。

附個人設定檔，可直接套用。

---

### [Skills 推薦收藏](skills/collection.md)

整理值得安裝的 Claude Code Skills，附功能說明與適用情境，涵蓋：

- 開發方法論
- 任務規劃
- 前端 UI 設計
- 影片製作（Remotion）
- 圖表製作與速成解釋（[eli5 × lieflat-charts](skills/eli5-lieflat-charts.md) 怎麼配合）

---

## 說明

內容僅記錄個人設定與使用心得，插件與 Skills 的版權歸各原作者所有。
