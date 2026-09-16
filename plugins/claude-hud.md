# claude-hud — Status Bar Plugin

> 插件由 [jarrodwatts](https://github.com/jarrodwatts/claude-hud) 開發，以下為個人設定分享

在 Claude Code 終端機下方顯示一條常駐狀態列，即時呈現目前 session 的狀態，不用輸入指令就能掌握：

- 目前使用的模型
- Context 視窗剩餘空間（視覺化進度條）
- Token 用量與費用
- Agent 執行狀態
- Git 分支名稱
- Session 時長、速度等資訊

---

## 安裝步驟

1. 新增市場：`/plugin marketplace add jarrodwatts/claude-hud`
2. 安裝插件：`/plugin install claude-hud`
3. 執行設定：`/claude-hud:setup`（會自動設定 statusLine 並啟用）
4. 重啟 Claude Code
   > 重啟後沒看到 bar 出現，可能是 bug，請 Claude Code 除錯

5. 將以下內容存到 `~/.claude/plugins/claude-hud/config.json`（覆蓋原本的）

---

## 設定檔

```json
{
  "lineLayout": "compact",
  "showSeparators": false,
  "gitStatus": {
    "enabled": true,
    "showDirty": false,
    "showAheadBehind": false,
    "showFileStats": false
  },
  "display": {
    "showModel": true,
    "showContextBar": true,
    "showTools": false,
    "showAgents": true,
    "showTodos": false,
    "showProject": false,
    "showConfigCounts": true,
    "showTokenBreakdown": false,
    "showSpeed": false,
    "showUsage": true,
    "usageBarEnabled": false,
    "usageCompact": true,
    "sevenDayThreshold": 0,
    "showSessionName": false,
    "showDuration": false,
    "customLine": ""
  }
}
```

---

## 7 天（週）用量預設會被藏起來

`display.sevenDayThreshold`（外掛預設 **80**）：只有 7 天用量百分比達到這個門檻，狀態列才會多顯示一段「週用量」；沒到門檻時，狀態列只會顯示 5 小時視窗，看起來像是完全沒有 7 天視窗，其實資料一直都有在追蹤，只是被這個門檻藏住了。

改成 `"sevenDayThreshold": 0` 就會一律顯示 7 天用量（不論百分比高低）。想恢復成「只有接近上限才提醒」的預設行為，把這個鍵刪掉或改回 `80` 即可。

## 用量顯示太長會自動換行

外掛會偵測終端機實際寬度，狀態列超過寬度就自動換成第二行——不是刻意設計成兩行，純粹是字數塞不下。同時顯示 5 小時＋7 天用量時很容易觸發這個情況。

`display.usageCompact`（預設 `false`）：開啟後格式從

```
Usage 5h 20% (resets in 3h 48m) | Weekly 6% (resets in 3d 14h)
```

變成

```
5h: 20% (3h 48m) | 7d: 6% (3d 14h)
```

拿掉「Usage」前綴、「Weekly」縮成「7d」、「resets in」的措辭整個消失（精簡格式本來就不含這幾個字），字數少很多，比較容易擠回同一行。

---

## 目前開啟的功能

| 功能 | 說明 |
|------|------|
| Model | 目前使用的模型名稱 |
| Context bar | Context 視窗使用量（視覺化） |
| Agents | 子 agent 執行狀態 |
| Config counts | 目前載入的設定數量 |
| Usage | Token 用量與費用（文字格式） |
| Git branch | 目前 git 分支名稱 |
| 7 天用量門檻 | 設為 0，7 天用量一律顯示（見上方說明） |
| 用量精簡格式 | 設為 true，拿掉「Usage/Weekly/resets in」等字，避免換行（見上方說明） |

---

## 目前關閉的功能

| 功能 | 說明 | config 鍵 |
|------|------|-----------|
| Separators | 各項目之間的分隔線 | `showSeparators` |
| Tools | 本次 session 使用的工具次數 | `showTools` |
| Todos | Todo 項目完成進度 | `showTodos` |
| Project | 專案名稱 | `showProject` |
| Token breakdown | Input / Output / Cache token 各別數量 | `showTokenBreakdown` |
| Speed | 輸出速度（tokens/s） | `showSpeed` |
| Usage bar | 費用用量（視覺化 bar 格式，與 Usage 文字版擇一） | `usageBarEnabled` |
| Session name | Session 名稱 | `showSessionName` |
| Duration | Session 持續時間 | `showDuration` |
| Custom line | 自訂文字列 | `customLine` |
| Git dirty | 未提交的異動檔案數 | `gitStatus.showDirty` |
| Git ahead/behind | 與遠端分支的 commit 差距 | `gitStatus.showAheadBehind` |
| Git file stats | 新增／修改／刪除的檔案統計 | `gitStatus.showFileStats` |

---

## 調整設定的方式

**推薦**：直接對 Claude Code 說要調整哪些項目，會自動修改設定：

```
/claude-hud:configure
```

**手動**：直接編輯 `~/.claude/plugins/claude-hud/config.json`，將對應鍵改為 `true` / `false`
