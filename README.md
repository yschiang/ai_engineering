# AI-Native Software Engineering Framework

這個 repository 提供一套部門級、tool-agnostic 的 AI engineering operating model，讓 Engineer 使用 AI 時仍維持清楚的問題定義、bounded change、human accountability 與 fresh evidence。

核心工作方式只有一條：

```text
Research → Design → Plan → Implement → Validate
```

> 不需要依編號從 `00` 讀到 `06`。先依角色選閱讀路徑，再回到既有 ticket、code、PR、test 與 release workflow 工作。

## Start Here in 5 Minutes

1. 先在下方選擇與角色相符的閱讀路徑；`00–06` 是 artifact identifiers，不是閱讀順序。
2. 第一次接觸 Framework 時，可先用 [Framework Overview](guides/04_Framework_Overview.md) 建立五分鐘視覺概覽；它是 optional summary，不是正式規則的前置文件。
3. Engineer 打開 [Golden Engineering Playbook](03_Golden_Engineering_Playbook.md) 的 §1，再直接閱讀與目前工作相符的章節：Feature 看 §8；P0／Bug／Refactor／Spike 看 §9；常見入口看 §13。
4. 不知道下一個 skill、是否使用 OpenSpec／Superpowers，直接查 [Decision Tree §6 — Choose the Next Capability](guides/05_Decision_Tree.md#6-choose-the-next-capability)；Work Level、risk 或 gate 不清楚時再查其他章節。
5. 使用 Golden default capability 前，先在 [Golden Skill Registry](reference/Golden_Skill_Registry.md) 確認它是可直接使用的 manual default、approved installable implementation，或尚未核准的 candidate。

第一次可以從一個 bounded P0 Bug 開始：

```text
Reproduce
→ Systematic Debugging
→ Regression Test
→ Minimal Fix
→ Review
→ Fresh Verification
```

Skill 選擇先看兩件事：

| 要做什麼已清楚？ | 需要跨 session／AI／Engineer 保存工程上下文？ | Default |
|---|---|---|
| 否 | 尚未判斷 | Research／`grill-me`／`/opsx:explore`，先把未知弄清楚 |
| 是 | 否 | **Fast Delivery**：Superpowers／Team equivalent end-to-end，直接完成 design、plan、TDD、request/receive code review、verification |
| 是 | 是 | **Complex / Durable Change**：OpenSpec 管 spec/tasks；以 `/opsx:apply` 選擇 task，逐 task 使用 Superpowers TDD/review；只留一份 SSOT |

Team 可依既有 workflow、工具可用性、熟悉度與交接頻率選 Fast Delivery 或 Complex/Durable Change。尚未清楚時先處理第一個未知，再回來二選一；Discovery 是 pre-route，不是第三條 delivery flow。客觀 architecture/risk/evidence 要求仍優先。

## Choose Your Reading Path

### Engineer

```text
README
→ 03 Golden Engineering Playbook：§1 + 對應工作章節
→ 開始工作
→ routing 不確定時查 05 Decision Tree
```

`03_Golden_Engineering_Playbook.md` 是 Engineer execution SSOT。Engineer 每次應閱讀與目前工作相符的章節，但不需要在第一次使用前全文讀完。

Optional：第一次接觸 Framework 時，可先看 `04 Framework Overview`。

### Senior Engineer / Tech Lead / Architect

```text
README
→ 02 Framework
→ 03 Golden Engineering Playbook
→ routing／risk／gate 不確定時查 05 Decision Tree
```

Optional：只想先取得五分鐘概覽時，可先看 `04 Framework Overview`；它不是閱讀 `02` 的必要前置步驟。

### Manager / Sponsor

```text
README
→ 00 Project Charter
→ 04 Framework Overview
→ 需要治理細節時查 02 Framework
```

Optional：參與或主持 Department meeting、onboarding workshop 或 Team training 時使用 `06 Training Presentation`。

### Framework Maintainer

```text
README
→ 00 Project Charter
→ 01 AI Handoff
→ 02 Framework
→ 03 Golden Engineering Playbook
→ 只檢查本次變更影響的 04–06 supplements
```

### Continuing AI Working Session

```text
01 AI Handoff
→ 依 Exact Next Action 讀取相關 SSOT
→ 只檢查本次變更影響的 04–06 supplements
```

`01_AI_Handoff.md` 是 Framework maintainer 與後續 AI working session 的工作狀態／決策交接，不是 Engineer onboarding 或日常操作文件。Continuing session 不必每次重讀所有 supplements。

## Artifact Guide

Artifact Guide 是文件選擇器，不是另一條閱讀順序。

| Artifact | 定位 | 何時使用 | 主要讀者 | 使用方式 |
|---|---|---|---|---|
| [`README.md`](README.md) | Repository navigation entry | 第一次進入 repo、確認角色路徑與文件位置 | 所有人 | **Required entry** |
| [`00_Project_Charter.md`](00_Project_Charter.md) | Project intent／scope SSOT | 判斷專案目的、scope、success criteria、decision rights | Sponsor、Manager、Framework Maintainer | 對治理角色 Required |
| [`01_AI_Handoff.md`](01_AI_Handoff.md) | Framework maintenance state SSOT | 延續 Framework 維護工作、確認 current status、decisions、next action | Framework Maintainer、AI working session | 一般 Engineer 跳過 |
| [`02_Framework.md`](02_Framework.md) | Methodology／governance SSOT | 查正式定義、risk、Execution Mode、gates、roles、DoD、adoption governance | Tech Lead、Architect、Manager、Framework Maintainer | 治理與設計決策時 Required |
| [`03_Golden_Engineering_Playbook.md`](03_Golden_Engineering_Playbook.md) | Engineer execution SSOT | 實際執行 Feature、Bug、Migration、Design、Implement、Validate | Engineer、Senior Engineer、Tech Lead | 對應工作章節 Required |
| [`guides/04_Framework_Overview.md`](guides/04_Framework_Overview.md) | Optional visual summary | 五分鐘理解 Golden Flow、向主管或新進成員說明整體模型 | 所有人 | Optional；不是 SSOT |
| [`guides/05_Decision_Tree.md`](guides/05_Decision_Tree.md) | Detailed routing reference | Work Level、Stage、risk、OpenSpec、skill 或 gate 判斷不清楚 | Engineer、Reviewer、Tech Lead | 按需查詢；不是主要操作手冊 |
| [`training/06_Training_Presentation.pptx`](training/06_Training_Presentation.pptx) | Facilitated training material | Department meeting、onboarding workshop、Team training | Trainer、Manager、Engineer | Training 時使用；不是 SSOT |
| [`reference/Golden_Skill_Registry.md`](reference/Golden_Skill_Registry.md) | Capability readiness／implementation provenance SSOT | 確認 manual default、skill source、支援環境、安裝、invocation、version 與 fallback | Engineer、Team Maintainer、Framework Maintainer | 使用或維護 capabilities 時 Required |

最重要的定位區分：

```text
02 = 正式方法與治理規則
04 = 由 02／03 衍生的快速視覺摘要

03 = Engineer 如何執行
05 = 判斷不清楚時的詳細 routing reference

06 = Facilitated training material
不是 Framework 或 execution SSOT
```

若文件內容衝突，以 Artifact Guide 標示的對應 SSOT 為準。`04–06` 是由 core documents 衍生的 understanding、routing 與 training views，不建立新的方法或規則。Decision Tree 的開頭同時擔任日常 quick reference；不另外維護一份重複的 `07` content SSOT。
