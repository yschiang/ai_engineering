# AI-Native Software Engineering Framework

這個 repository 提供一套部門級、tool-agnostic 的 AI engineering operating model，讓 Engineer 使用 AI 時仍維持清楚的問題定義、bounded change、human accountability 與 fresh evidence。

核心工作方式只有一條：

```text
Research → Design → Plan → Implement → Validate
```

> 不需要依編號從 `00` 讀到 `06`。先依角色選閱讀路徑，再回到既有 ticket、code、PR、test 與 release workflow 工作。

## Start Here in 5 Minutes

1. 用 [Framework Overview](guides/04_Framework_Overview.md) 建立 Golden Flow 與 Six Golden Questions 的整體認知。
2. 打開 [Golden Engineering Playbook](03_Golden_Engineering_Playbook.md) 的 §1，確認 Work Level、Archetype、Current Stage 與 Control Profile。
3. 直接閱讀與目前工作相符的章節：Feature 看 §8；P0／Bug／Refactor／Spike 看 §9；常見入口看 §13。
4. 只有在 Work Level、risk、stage、OpenSpec 或 gate 判斷不清楚時，才查 [Decision Tree](guides/05_Decision_Tree.md)。
5. 啟動 Golden default skill 前，先在 [Golden Skill Registry](reference/Golden_Skill_Registry.md) 確認 source、安裝狀態、invocation 與 fallback。

第一次可以從一個 bounded P0 Bug 開始：

```text
Reproduce
→ Systematic Debugging
→ Regression Test
→ Minimal Fix
→ Review
→ Fresh Verification
```

## Choose Your Reading Path

### Engineer

```text
README
→ 04 Framework Overview
→ 03 Golden Engineering Playbook：§1 + 對應工作章節
→ 開始工作
→ routing 不確定時查 05 Decision Tree
```

`03_Golden_Engineering_Playbook.md` 是 Engineer execution SSOT。Engineer 每次應閱讀與目前工作相符的章節，但不需要在第一次使用前全文讀完。

### Senior Engineer / Tech Lead / Architect

```text
README
→ 04 Framework Overview
→ 02 Framework
→ 03 Golden Engineering Playbook
→ 05 Decision Tree
```

### Manager / Sponsor

```text
README
→ 00 Project Charter
→ 04 Framework Overview
→ 06 Training Presentation
→ 需要治理細節時查 02 Framework
```

### Framework Maintainer / AI Working Session

```text
01 AI Handoff
→ 00 Project Charter
→ 02 Framework
→ 03 Golden Engineering Playbook
→ 04–06 supplements
```

`01_AI_Handoff.md` 是 Framework maintainer 與後續 AI working session 的工作狀態／決策交接，不是 Engineer onboarding 或日常操作文件。

## Artifact Guide

| Artifact | 具體用途 | 何時使用 | 主要讀者 |
|---|---|---|---|
| [`00_Project_Charter.md`](00_Project_Charter.md) | 定義 Why、Scope、目標、成功標準與治理 | 確認專案方向、scope 或 decision rights | Sponsor、Manager、Framework Maintainer |
| [`01_AI_Handoff.md`](01_AI_Handoff.md) | 保存 Framework 工作狀態、已確認決策與下一步 | AI session／Maintainer 繼續維護 Framework | AI、Framework Maintainer；一般 Engineer 可跳過 |
| [`02_Framework.md`](02_Framework.md) | Methodology 與 Governance SSOT | 查 Golden Flow 定義、risk、AI authority、gates、roles、DoD | Tech Lead、Architect、Manager |
| [`03_Golden_Engineering_Playbook.md`](03_Golden_Engineering_Playbook.md) | Engineer execution SSOT | 實際執行 Feature、Bug、Migration、Design、Implement、Validate | Engineer、Tech Lead |
| [`guides/04_Framework_Overview.md`](guides/04_Framework_Overview.md) | 一頁呈現整體 mental model | 第一次接觸、onboarding、主管說明、training 開場 | 所有人 |
| [`guides/05_Decision_Tree.md`](guides/05_Decision_Tree.md) | 詳細 routing reference；開頭是 compact router | 分類、risk、stage、OpenSpec 或 next move 不清楚 | Engineer、Reviewer、Tech Lead |
| [`training/06_Training_Presentation.pptx`](training/06_Training_Presentation.pptx) | Facilitated training deck | Department meeting、onboarding workshop、Team training | Trainer、Manager、Engineer |
| [`reference/Golden_Skill_Registry.md`](reference/Golden_Skill_Registry.md) | Golden skills 的 source、環境、安裝、invocation、fallback | 啟用或維護 Golden default skills | Engineer、Team Maintainer、Department Maintainer |

## Source of Truth

| Question | Source of Truth |
|---|---|
| Project intent、scope、success | `00_Project_Charter.md` |
| Working status、confirmed decisions、next maintenance action | `01_AI_Handoff.md` |
| Method、risk、governance、roles、gates、DoD | `02_Framework.md` |
| Engineer execution、skills、artifacts、stage guidance | `03_Golden_Engineering_Playbook.md` |
| Detailed routing | `guides/05_Decision_Tree.md` |
| Skill provenance and environment mapping | `reference/Golden_Skill_Registry.md` |

`04–06` 是由 core documents 衍生的 understanding、routing 與 training views，不建立新的方法或規則。Decision Tree 的開頭同時擔任日常 quick reference；不另外維護一份重複的 `07` content SSOT。

## Repository Layout

```text
/
├── README.md
├── 00_Project_Charter.md
├── 01_AI_Handoff.md
├── 02_Framework.md
├── 03_Golden_Engineering_Playbook.md
├── guides/
│   ├── 04_Framework_Overview.md
│   └── 05_Decision_Tree.md
├── training/
│   ├── 06_Training_Presentation.pptx
│   └── assets and rendered review artifacts
└── reference/
    └── Golden_Skill_Registry.md
```
