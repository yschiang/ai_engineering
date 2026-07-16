# Project Charter — AI-Native Software Engineering Framework

> Version: v1.3 Baseline  
> Status: Active  
> Project Sponsor: Department Head  
> Primary Audience: Division Head, CIO, Engineering Management, Architects, Engineering Teams  
> Working Language: Traditional Chinese with English engineering terms

---

## 1. Project Name

**AI-Native Software Engineering Framework**

本專案建立一套部門級、可落地、可治理、可持續演進的 AI engineering operating model。

---

## 2. Executive Intent

AI coding 正在快速降低程式實作門檻，但真正限制 enterprise software delivery 的，仍然是：

- 是否理解正確的系統與問題。
- 是否做出合理的 architecture 與 engineering decision。
- 是否能證明 change 正確、安全且可維運。
- 是否能將個人經驗轉化為團隊可重複使用的能力。

本專案不是推廣單一 AI 工具，而是重新定義 AI 時代的軟體工程工作方式。

最終目標是讓 AI 參與從 system understanding、problem definition、design、implementation、verification 到 release 與 operation 的完整 lifecycle，同時維持 production safety、architecture integrity 與 human accountability。

---

## 3. Problem Statement

團隊已開始使用各類 AI coding tools，但缺乏共同框架會產生以下問題：

1. 使用方式集中在 code generation，沒有覆蓋完整 engineering lifecycle。
2. Engineer 在 system understanding 與 requirement clarification 不足時直接修改 code。
3. AI 能快速產生大量 change，但 human review、testing 與 operational readiness 無法同步擴張。
4. 不同 team 各自發明 workflow，成功經驗無法複製，失敗模式重複發生。
5. 低風險 automation 與 production-critical change 缺乏差異化治理。
6. Management 容易以工具使用率、prompt 數或 AI-generated LOC 衡量 adoption，而不是 engineering outcome。
7. 重要 context 與 decision 留在 chat 中，沒有沉澱為 tests、rules、templates、runbooks 或 architecture assets。

若沒有共同 framework，AI 會同時放大 delivery speed 與 engineering risk。

---

## 4. Vision

建立一個 **Enterprise-grade、Tool-agnostic、Capability-based** 的 AI-Native Software Engineering Framework，使團隊能：

- 更快理解複雜與 legacy systems。
- 更準確地定義 problem、scope 與 acceptance criteria。
- 使用 AI 挑戰 requirement、design 與 implementation。
- 以 bounded、reviewable、reversible 的方式完成 change。
- 以 evidence 而不是 AI confidence 判斷 quality 與 release readiness。
- 依 project risk 分級治理，不增加不必要流程。
- 將成功經驗沉澱成可重用 engineering assets。

---

## 5. Strategic Positioning

### 5.1 Enterprise-grade

Framework 必須適用於正式 software products、shared platforms 與 production-critical systems，而不只適用於 prototype 或 personal productivity。

### 5.2 Tool-agnostic

Framework 不綁定 Claude Code、Codex、Gemini 或其他特定工具。工具可以替換，engineering principles、artifacts 與 evidence 必須可延續。

### 5.3 Capability-based

Framework 以工程能力組織內容，而不是以 prompt type 或產品功能組織內容。

### 5.4 Risk-based

控制強度依 change impact 與 uncertainty 調整。低風險工作保持輕量；高風險工作強化 design、review、verification、release 與 recovery evidence。

### 5.5 Consulting-grade and Engineering-practical

Framework 的結構與論述需具備 McKinsey／BCG 等級的清晰度，能向 Division Head 與 CIO 說明；內容同時必須能被 Engineer、Architect 與 Manager 直接使用。

---

## 6. Objectives

### O1. 建立共同語言

定義 AI-Native Engineering 的 lifecycle、work loop、risk tier、quality gates、roles 與 Definition of Done。

### O2. 建立可執行方法

讓各種 engineering work 能依一致模式進行：

`Understand → Challenge → Execute → Evidence`

並提供 Engineer 可直接使用的五階段 Golden Flow：

`Research → Design → Plan → Implement → Validate`

每個 Delivery Level 與 Work Archetype 都明確定義 lead skill、minimum artifact 與 human gate。

### O3. 建立風險與執行分級治理

以 `System Criticality × L0–L3 Change Risk Tier × E0–E3 AI Execution Mode` 決定必要 design、review、testing、authorization、release 與 operational controls。

### O4. 建立可重用資產

將成功做法沉澱為 Framework、Golden Engineering Playbook、overview、decision tree、training deck、quick reference、templates、tests、rules 與 runbooks。

### O5. 建立管理衡量方式

以 lead time、quality、reliability、knowledge flow 與 engineering efficiency 衡量 adoption outcome。

### O6. 支援組織規模化

讓 AI adoption 從個人 power user，轉變為 team capability 與 department operating model。

---

## 7. Scope

### 7.1 In Scope

- AI-Native Software Engineering 的核心原則。
- End-to-end Engineering Lifecycle。
- AI Work Loop 與 reusable working patterns。
- L0–L3 Change Risk Tier、System Criticality 與 E0–E3 AI Execution Mode。
- Requirement、design、implementation、review、testing、release、operation 的 AI collaboration practices。
- Engineer、Senior Engineer、Tech Lead、Architect、Manager、Department Head 的責任。
- Quality Gates、Definition of Done 與 evidence model。
- Adoption model、metrics 與 management system。
- P3 Product/Program、P2 Epic、P1 Feature、P0 PBI/User Story 的 Delivery Level，以及 P0 下方 Execution Layer 的 decomposition rules。
- Greenfield Product、Legacy Modernization/Migration、Standard Delivery 的 Work Archetype flows。
- Research、Design、Plan、Implement、Validate 的 skill → artifact → gate mapping。
- Framework repository 與 input/output/reference/archive 結構。
- 部門 training 與 quick-reference materials。

### 7.2 Out of Scope

- 指定或採購單一 AI coding product。
- 特定工具的完整操作手冊。
- 建立大型 prompt library 作為本 Framework 的核心。
- 取代現有 SDLC、Architecture、Security、DevOps、SRE、Change 或 Incident processes。
- 定義公司機密資料與 AI 工具使用政策；本 Framework 僅要求遵循既有 approved policy。
- 將所有專案強制套用同一份重量級文件與 checklist。
- 以 AI output percentage 或 generated LOC 作為績效制度。
- 將 production decision 或 engineering accountability 交給 AI。

---

## 8. Target Audience

| Audience | Framework Value |
|---|---|
| Engineer | 如何與 AI 安全完成真實 engineering task |
| Senior Engineer / Tech Lead | 如何定義問題、建立方法、review risk、沉澱 patterns |
| Architect | 如何維持 boundary、contract、data ownership 與 architecture integrity |
| Engineering Manager | 如何選 use case、建立 team capability、衡量 outcome |
| Department Head | 如何形成 portfolio、governance 與 adoption operating model |
| Division Head / CIO | 如何理解 AI engineering 對 delivery、quality、reliability 與組織能力的影響 |

---

## 9. Core Framework Hypothesis

本專案基於以下假設：

1. AI 最有價值的用途不只是寫 code，而是參與完整 engineering lifecycle。
2. AI 會放大既有工程方法；好的方法被放大，模糊需求與不良設計也會被放大。
3. Human review capacity 不會隨 AI output 線性增加，因此 change 必須保持 bounded and reviewable。
4. High-risk systems 需要更強 evidence，而不是禁止使用 AI。
5. Senior engineer 的價值將更集中於 problem definition、domain judgment、engineering method 與 reusable guardrails。
6. 可持續的 adoption 來自 workflow、assets 與 management system，而不是一次性 training。

---

## 10. Design Principles

1. **Engineering Outcome and Human Accountability**
2. **Context before Action**
3. **Controlled Change and Architecture Integrity**
4. **Risk-based Evidence**
5. **Reusable Learning**

詳細定義由 `02_Framework.md` 管理。

---

## 11. Expected Deliverables

`00–07` 共八個 artifacts。`00–03` 是 core operating assets；`04–07` 是由 core 衍生、幫助理解、判斷、training 與日常使用的 supplements。

| ID | Artifact | Format | Purpose |
|---|---|---|---|
| 00 | Project Charter | Markdown | 定義 Why、Scope、Principles、Success Criteria |
| 01 | AI Handoff | Markdown | 後續 AI working sessions 的 SSOT 與執行規則 |
| 02 | AI-Native Software Engineering Framework | Markdown，約 25–30 頁 | 完整方法論母文件 |
| 03 | Department Golden Engineering Playbook | Markdown | 依 Delivery Level / Archetype / Stage 導向 skills、artifacts、gates 的工程師 Golden Reference |
| 04 | Framework Overview | Diagram / Markdown | 一頁呈現 Framework 與 Golden Flow |
| 05 | Decision Tree | Diagram / Markdown | 判斷 Work Level、Archetype、Tier、stage、skills 與 controls |
| 06 | Training Presentation | PowerPoint，約 8–10 頁 | 用真實 scenarios 進行部門溝通與教育訓練 |
| 07 | Quick Reference Guide | One Pager | 工程師與 Manager 日常快速使用 |

Bonus artifacts，例如 prompt matrix、case library 或 detailed templates，需在核心交付物完成後再決定。

---

## 12. Repository Blueprint

```text
/
├── 00_Project_Charter.md
├── 01_AI_Handoff.md
├── 02_Framework.md
├── 03_Golden_Engineering_Playbook.md
├── diagrams/
│   ├── 04_Framework_Overview.*
│   └── 05_Decision_Tree.*
├── presentation/
│   └── 06_Training_Presentation.pptx
├── templates/
│   └── 07_Quick_Reference_Guide.*
├── assets/
├── input/
├── output/
├── reference/
└── archive/
```

詳細 I/O rules 由 `02_Framework.md` 管理。

---

## 13. Success Criteria

### 13.1 Artifact Quality

- Framework 具備 executive clarity 與 engineering depth。
- 八份 artifacts 使用同一 capability model、Delivery Level、Tier、terminology 與 governance logic。
- Golden Playbook 能讓 Engineer 在 60 秒內找到 current stage、lead skill、minimum artifact 與 gate。
- Decision Tree 與 Quick Reference 能在日常工作中直接使用。
- Training Presentation 能在 8–10 頁內完成管理與工程溝通。

### 13.2 Engineering Adoption

- Team 能使用 Framework 完成真實 engineering tasks。
- Engineer 能從理解、挑戰、執行到 evidence 完成閉環。
- Control Profile 能有效區分 system criticality、change risk 與 AI action authorization。
- Mandatory practice 維持最小必要，不形成文件負擔。

### 13.3 Outcome Improvement

- Time to first safe change 縮短。
- Requirement/design rework 降低。
- Lead time 改善，且 escaped defect/change failure rate 不惡化。
- Incident、legacy knowledge 與 domain rules 能轉化為 reusable assets。
- 成功方法可跨 team 重複使用。

---

## 14. Constraints

- 使用 Traditional Chinese，保留必要 English engineering terms。
- 內容需適合 semiconductor manufacturing IT 與 production-critical contexts，但不得只適用單一產品。
- Framework 必須能覆蓋 inline critical systems、shared platforms 與一般 engineering automation。
- 不以特定 AI 工具能力作為 framework dependency。
- 每個 activity 的 universal mandatory controls 原則上不超過三項，其餘依 Tier 與 risk 觸發。
- `02_Framework.md` 是方法與治理 SSOT；`03_Golden_Engineering_Playbook.md` 是流程、skill mapping 與工程使用 SSOT。
- `04–07` supplements 必須由 `02` 與 `03` 衍生，不得自行增加新方法。

---

## 15. Key Risks and Responses

| Risk | Response |
|---|---|
| Framework 太抽象，無法執行 | 提供 Golden Playbook、level/archetype flows、skill mapping、gates、templates 與 examples |
| Framework 太重，團隊不採用 | Risk-based tiering；mandatory controls 最小化 |
| 內容退化成工具教學 | 堅持 tool-agnostic、capability-based positioning |
| AI 加速 output 但 quality 下降 | Evidence Gate、human accountability、balanced metrics |
| 不同 artifacts 內容漂移 | `02_Framework.md` 作為內容 SSOT；版本化同步更新 |
| 只由少數 power users 掌握 | Training、quick reference、team missions、reusable assets |
| Management 只看使用率 | 以 delivery、quality、reliability 與 knowledge flow 衡量 |

---

## 16. Governance and Decision Rights

| Decision | Owner |
|---|---|
| Project intent、scope 與 success criteria | Department Head / Sponsor |
| Framework model 與 engineering standards | Framework Owner + Architecture/Engineering reviewers |
| Tool selection 與 enterprise policy | Existing organizational owners，不由本專案取代 |
| Team implementation pattern | Product/Engineering team，在 Framework guardrails 內決定 |
| L2–L3 design/release decision | Existing accountable engineering and service owners |
| Artifact release | Framework Owner |

---

## 17. Milestones

| Milestone | Deliverable | Completion Condition |
|---|---|---|
| M0 | Charter + Handoff | Direction、scope、working rules 確認 |
| M1 | Framework | 核心 model、Tier、lifecycle、roles、gates、DoD 完整 |
| M2 | Golden Engineering Playbook | P3–P0 與三種 archetype 的 skill → artifact → gate flow 可直接使用 |
| M3 | Overview + Decision Tree | 能一頁理解、能快速做 work/risk/workflow decision |
| M4 | Training Presentation | 可供部門 training 使用的 PowerPoint |
| M5 | Quick Reference | 可供日常工作使用的 one pager |
| M6 | Pilot and Revision | 由真實 use cases 驗證並完成 revision |

---

## 18. Project Definition of Done

專案完成需滿足：

1. `00–07` artifacts 全部完成並可被使用。
2. 各 artifact 之 capability model、Tier、quality gates 與 terminology 一致。
3. Framework 經 Engineering、Architecture 與 Management perspectives review。
4. 至少以 Greenfield、Modernization/Migration、Feature、Bug/Incident 各一組真實 use case 驗證 Playbook、Decision Tree 與 Quick Reference。
5. Feedback 已轉為明確 revision，不保留 blocking ambiguity。
6. 文件具備 version、owner、status 與後續 governance mechanism。

---

## 19. Charter Statement

本專案的核心，不是讓更多人更快產生 code，而是建立一套新的工程能力：

> **讓團隊更快理解正確的問題、做出更好的 engineering decision，並用足夠 evidence 安全交付。**
