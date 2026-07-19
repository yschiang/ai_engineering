# E1 PR Decision Record — Adoption Reference

> Status: 30-day pilot reference
> Scope: One Team／repository at a time
> Not a new lifecycle, approval system, form or dashboard

E1 的目的只有一個：讓 Human Gate decision 在既有 PR chokepoint 可追溯，而且不增加 P0 負擔。

此處 **E1 = Enforcement rollout 1**，不是 Framework 的 AI Execution Mode E1。

> **先讓一個 Team 用起來。只有 E1 啟用；其他 detection 定義後保持關閉。**

## Start in One Day

1. 選一個 pilot Team／repository 與一位 Tech Lead owner。
2. 確認既有 branch protection／ruleset 已要求至少一位非 author Human approval；它就是 P0 的 decision record。
3. 複製 [`human-decision-record.yml`](enforcement/e1/human-decision-record.yml) 到 pilot repo 的 `.github/workflows/`。
4. 若 Team 已有可機器辨識的 P0 label，把它填入 workflow 的 `P0_LABELS`；沒有就留空，先採 approval-only mode，**不要為 automation 新增 P0 欄位**。
5. 為非 P0 PR 建立 `gate:pass`、`gate:conditional`、`gate:rework` 三個 labels。
6. 用 [`example-pr.md`](enforcement/e1/example-pr.md) 跑 2–3 個 PR；確認 mapping 正確後，才把 `human-decision-record` 設成 pilot branch 的 required check。
7. Required check 啟用日起算 30 天；到期前不擴大其他 enforcement。

文件只供查細節。Tech Lead 的 adoption path 是：**copy workflow → run example PR → enable one required check**。

## E1 Rule

| PR situation | Human record | Bot result |
|---|---|---|
| P0 | Existing PR approval；不要求 gate label 或新欄位 | Pass；approval 由既有 branch protection enforce |
| Non-P0 Pass | Current PR approval + `gate:pass` | Pass |
| Non-P0 Conditional Pass | Current PR approval + `gate:conditional` + PR body 的 `Condition tracking: #123` | Pass |
| Rework | `gate:rework` | Block |
| Non-P0 missing/conflicting gate labels | — | Block |

Bot 只檢查 machine-detectable presence，不判斷 design 是否正確、evidence 是否充分或 risk 是否值得接受。這些仍由 Human Reviewer accountable。

## Detection Classification

| Department rule | Detection | Rollout state |
|---|---|---|
| Human Decision Record on PR | **Blocking**：approval 由既有 ruleset；bot 檢查 non-P0 label／conditional issue | **E1 active for pilot only** |
| Team profile 不得降低 required gates | **Sampling**：需要 Human judgment | Defined；not enabled |
| OpenSpec／Superpowers no dual SSOT | **Detective**：path heuristic 只能提示，不能判斷合理引用 | Defined；not enabled |

不要為了自動化，把 Sampling rule 假裝成 Blocking rule。

## What the Workflow Does

- 使用 `pull_request_target` 讀取 trusted default-branch workflow；不 checkout、下載或執行 PR code。
- 權限只有 `contents: read`、`pull-requests: read`、`issues: read`。
- P0 label mapping 留空時採 approval-only mode，讓 Team 先 adoption。
- 有 P0 mapping 時，P0 直接通過 bot；non-P0 才檢查 gate label。
- Conditional Pass 只接受明確的 `Condition tracking:` issue reference。

正式採用前，Team 仍應依 [GitHub secure use of `pull_request_target`](https://docs.github.com/en/actions/reference/security/securely-using-pull_request_target) review workflow；不得加入 checkout PR head、執行 PR code、write token 或 secrets。

## 30-Day Review

不建立 dashboard。沿用 Actions logs、PR history 與一張既有 rollout issue：

- 記錄 Team-level friction：最常失敗原因、修正一次需要多久。
- 在 rollout issue 記錄 confirmed false positives 與必要調整。
- 抽樣檢查 Human approval、label 與 linked issue 是否真的可理解。
- 不對個人排名、計分或比較。

第 30 天由 pilot Team 決定 **keep／adjust／stop**。只有 E1 friction 與 false positives 可接受時，才討論第二輪；不得自動擴大到其他 Team 或 detection。

## Known Limits

- 沒有既有 machine-readable P0 metadata 時，workflow 無法可靠區分 work level；approval-only mode 是刻意的 adoption fallback。
- Bot 能確認 label／issue link 存在，不能確認內容品質。
- GitHub labels、ruleset 與 PR body 是此 reference implementation；其他平台應 mapping 到既有 PR／CI／tracker chokepoints，不另建系統。
