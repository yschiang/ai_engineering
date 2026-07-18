# Project Charter — AI-Native Software Engineering Framework

> Version: v1.7 Baseline
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

最終目標是讓 Engineer 以單一 Golden Playbook 使用 AI，從 system understanding、problem definition、design、implementation 到 validation，並與既有 release／operation responsibility 接軌，同時維持 production safety、architecture integrity 與 human accountability。

---

## 3. Problem Statement

團隊已開始使用各類 AI coding tools，但缺乏共同框架會產生以下問題：

1. 使用方式集中在 code generation，沒有覆蓋理解、設計、驗證、release readiness 與 production learning 等完整工程責任。
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

### 5.6 Integrated with Existing SDLC

AI-Native Engineering 是既有 SDLC 的 enhancement layer，不建立平行 delivery process。現有角色、approval authority、release responsibility 與 production accountability 不因 AI 改變。

Golden Stages 是跨 Team 穩定的 engineering decision states，不是 Department 統一規定的 SDLC phases。每個 Team 自主管理 local workflow，並將既有 activities mapping 到所需 Golden questions、gates 與 artifact locations。

---

## 6. Objectives

### O1. 建立單一 Engineer Mental Model 與共同語言

以 `Research → Design → Plan → Implement → Validate` 作為唯一 Engineer-facing Golden Flow。每次進入新的 work item，Engineer 先用 Six Golden Questions 完成一次 initial routing：確認工作記在哪裡、Work Level、Archetype、current stage、Control Profile 與 next move。進入執行後，通常只需更新 current stage 與 next move；scope、architecture、risk 或 AI authority 改變時，再重新完成六題判斷。Six Golden Questions 是 routing contract，不形成第二套 workflow。

### O2. 建立可執行方法

讓各種 engineering work 都以同一 Golden Flow 進行：

`Research → Design → Plan → Implement → Validate`

在每個 Golden Stage，都練習同一組 AI 基本功：

`Understand → Challenge → Execute → Evidence`

每個 Delivery Level 與 Work Archetype 都明確定義 required capability、active default execution、minimum artifact 與 human gate。新手與尚未建立方法的 Team 直接採用 active default；成熟 Team 可 mapping 到 approved equivalent，但不得降低 capability、required input/output、stop condition、gate 或 evidence contract。

### O3. 建立風險與執行分級治理

以 `System Criticality × L0–L3 Change Risk Tier × E0–E3 AI Execution Mode` 決定必要 design、review、testing、authorization、release 與 operational controls。

### O4. 建立可重用資產與在地化能力

將成功做法沉澱為 Framework、Golden Engineering Playbook、overview、decision tree、training deck、skill registry、tests、rules、runbooks 與 case evidence。Department 定義 minimum artifact contract 與 quality bar；各 Team 擁有符合自身產品、技術棧與 workflow 的 templates。

### O5. 建立管理衡量方式

以 lead time、quality、reliability、knowledge flow 與 engineering efficiency 衡量 adoption outcome。

### O6. 支援組織規模化

讓 AI adoption 從個人 power user，轉變為 team capability 與 department operating model。

---

## 7. Scope

### 7.1 In Scope

- AI-Native Software Engineering 的核心原則。
- Golden Flow、Six Golden Questions 與 Team workflow integration。
- `Understand → Challenge → Execute → Evidence` AI 基本功與 reusable working patterns。
- 從 problem understanding 到 release／operation learning 的 engineering responsibility coverage；此 coverage 不構成另一套正式 lifecycle model。
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
- 與既有 SDLC、Agile、Architecture、DevOps、SRE、Release 與 Change Management 的 integration mapping。
- 既有十個以上 Department Head-led pilot cases 的 consolidation 與 canonical case selection。
- Department minimum artifact contract 與 Team-owned template governance。

### 7.2 Out of Scope

- 指定或採購單一 AI coding product。
- 特定工具的完整操作手冊。
- 建立大型 prompt library 作為本 Framework 的核心。
- 取代現有 SDLC、Architecture、Security、DevOps、SRE、Change 或 Incident processes。
- 定義公司機密資料與 AI 工具使用政策；本 Framework 僅要求遵循既有 approved policy。
- 將所有專案強制套用同一份重量級文件與 checklist。
- 由中央 Framework 統一設計所有 Team 的 tracker fields、repository instructions、technology checklist 或 product-specific templates。
- 重新要求執行已存在的 pilot，作為 Framework 才能成立的門檻。
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

1. AI 最有價值的用途不只是寫 code，而是增強理解、設計、執行、驗證與 production learning 的完整工程責任。
2. AI 會放大既有工程方法；好的方法被放大，模糊需求與不良設計也會被放大。
3. Human review capacity 不會隨 AI output 線性增加，因此 change 必須保持 bounded and reviewable。
4. High-risk systems 需要更強 evidence，而不是禁止使用 AI。
5. Senior engineer 的價值將更集中於 problem definition、domain judgment、engineering method 與 reusable guardrails。
6. 可持續的 adoption 來自 workflow、assets 與 management system，而不是一次性 training。
7. 部門一致性應來自 minimum information、evidence 與 traceability contract，而不是所有 Team 使用同一份模板。
8. Framework 已有十個以上實際 pilot cases 作為 evidence base；下一步是整理、對照與重用，不是重新建立 pilot 才能證明方法成立。

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

`00–06` 共七個 numbered artifacts。`00–03` 是 core operating assets；`04–06` 是由 core 衍生、幫助理解、判斷與 training 的 supplements。Root README 提供角色導覽；Skill Registry 管理 Golden skill provenance 與 environment mapping。

| ID | Artifact | Format | Purpose |
|---|---|---|---|
| 00 | Project Charter | Markdown | 定義 Why、Scope、Principles、Success Criteria |
| 01 | AI Handoff | Markdown | 後續 AI working sessions 的 SSOT 與執行規則 |
| 02 | AI-Native Software Engineering Framework | Markdown，約 25–30 頁 | 完整方法論母文件 |
| 03 | Department Golden Engineering Playbook | Markdown | 依 Delivery Level / Archetype / Stage 導向 skills、artifacts、gates 的工程師 Golden Reference |
| 04 | Framework Overview | Diagram / Markdown | 一頁呈現 Framework 與 Golden Flow |
| 05 | Decision Tree | Diagram / Markdown | 開頭提供 compact router，並詳細判斷 Work Level、Archetype、Tier、stage、skills 與 controls |
| 06 | Training Presentation | PowerPoint，約 10–12 頁 | 用真實 scenarios 進行部門溝通與教育訓練 |

Decision Tree 的開頭同時擔任日常 quick reference；不另行維護重複的 `07` content SSOT。若未來需要 PDF／PNG handout，應由 `05` 的 compact router 衍生，而不是建立第二套規則。

Case Library 是由既有 pilot 持續演進的 reference collection，不是新的 mandatory core artifact。Prompt matrix 或其他 bonus assets 應依真實 adoption need 決定；team-specific templates 由各 Team 維護，不由中央 Framework 大量建立。

---

## 12. Repository Blueprint

```text
/
├── README.md
├── 00_Project_Charter.md
├── 01_AI_Handoff.md
├── 02_Framework.md
├── 03_Golden_Engineering_Playbook.md
├── guides/
│   ├── 04_Framework_Overview.*
│   └── 05_Decision_Tree.*
├── training/
│   └── 06_Training_Presentation.pptx
└── reference/
    └── Golden_Skill_Registry.md
```

詳細 I/O rules 由 `02_Framework.md` 管理。

---

## 13. Success Criteria

### 13.1 Artifact Quality

- Framework 具備 executive clarity 與 engineering depth。
- 七份 numbered artifacts 使用同一 capability model、Delivery Level、Tier、terminology 與 governance logic。
- Golden Playbook 能讓 Engineer 在 60 秒內完成新工作的 Six Questions initial routing，找到 current stage、required capability、minimum artifact 與 gate；持續執行時只更新有變化的 routing fields。
- Decision Tree 的 compact router 與 detailed routing 能在日常工作中直接使用。
- Training Presentation 能在約 10–12 頁內完成管理與工程溝通。
- Root README 能依角色將讀者導向正確 SSOT；Skill Registry 能追溯 Golden default source、environment、invocation 與 fallback。

### 13.2 Engineering Adoption

- Team 能使用 Framework 完成真實 engineering tasks。
- Engineer 能在每個 Golden Stage 使用理解、挑戰、執行、留證據的 AI 基本功完成閉環。
- Control Profile 能有效區分 system criticality、change risk 與 AI action authorization。
- Mandatory practice 維持最小必要，不形成文件負擔。
- Engineer 能在既有 backlog、Sprint、design review、PR、test、release 與 operation workflow 中使用 Framework，不需要離開現有 SDLC 跑另一套流程。
- Team template 可因產品與技術棧不同，但在對應 risk level 下不得省略 Department minimum information 與 evidence contract。

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
- `04–06` supplements 必須由 `02` 與 `03` 衍生，不得自行增加新方法。

---

## 15. Key Risks and Responses

| Risk | Response |
|---|---|
| Framework 太抽象，無法執行 | 提供 Golden Playbook、level/archetype flows、skill mapping、gates、templates 與 examples |
| Framework 太重，團隊不採用 | Risk-based tiering；mandatory controls 最小化 |
| 內容退化成工具教學 | 堅持 tool-agnostic、capability-based positioning |
| AI 加速 output 但 quality 下降 | Evidence Gate、human accountability、balanced metrics |
| 不同 artifacts 內容漂移 | `02_Framework.md` 作為內容 SSOT；版本化同步更新 |
| 只由少數 power users 掌握，其他人停留在 vibe coding | Root README 角色路徑、active capability defaults、Training、Decision Tree compact router、Skill Registry 與 reusable assets；candidate skill 不阻塞 Research |
| Management 只看使用率 | 以 delivery、quality、reliability 與 knowledge flow 衡量 |
| Framework 被誤用為平行 SDLC | 將 capabilities、artifacts 與 gates 明確 mapping 到既有 intake、backlog、design、PR、test、release、change 與 operation activities |
| 中央模板過多，Team 難以採用 | Department 只定義 minimum contract；Team 自主管理 tracker fields、templates、repository instructions 與 local DoD |

---

## 16. Governance and Decision Rights

| Decision | Owner |
|---|---|
| Project intent、scope 與 success criteria | Department Head / Sponsor |
| Framework model 與 engineering standards | Framework Owner + Architecture/Engineering reviewers |
| Tool selection 與 enterprise policy | Existing organizational owners，不由本專案取代 |
| Team implementation pattern | Product/Engineering team，在 Framework guardrails 內決定 |
| Team template、tracker fields、repository instructions、technology/product checklist | Product/Engineering team；必須滿足 Department minimum contract |
| L2–L3 design/release decision | Existing accountable engineering and service owners |
| Artifact release | Framework Owner |

---

## 17. Milestones

| Milestone | Deliverable | Completion Condition |
|---|---|---|
| M0 | Charter + Handoff | Direction、scope、working rules 確認 |
| M1 | Framework | Golden model、responsibility coverage、Tier、roles、gates、DoD 完整 |
| M2 | Golden Engineering Playbook | Golden Flow + Six Questions，以及 P3–P0／archetype 的 capability → artifact → gate routing 可直接使用 |
| M3 | Overview + Decision Tree | 能一頁理解、能快速做 work/risk/workflow decision |
| M4 | Training Presentation | 可供部門 training 使用的 PowerPoint |
| M5 | Adoption Navigation + Skill Registry | Root README 可依角色導覽；Decision Tree 開頭可快速 routing；capability readiness、implementation source、environment、invocation 與 fallback 可追溯 |
| M6 | Existing Pilot Consolidation and Revision | 盤點十個以上既有 cases，選出 3–5 個 canonical cases，其餘進入持續演進的 Case Library |

---

## 18. Project Definition of Done

專案完成需滿足：

1. `00–06` numbered artifacts、Root README 與 Golden Skill Registry 全部完成並可被使用。
2. 各 artifact 之 capability model、Tier、quality gates 與 terminology 一致。
3. Framework 經 Engineering、Architecture 與 Management perspectives review。
4. 十個以上既有 pilot cases 已依 Work Level、Archetype、stage、risk、execution mode、artifacts/evidence、outcome 與 lessons learned 完成 mapping；選出 3–5 個 canonical cases 用於 Framework/Training。
5. Feedback 已轉為明確 revision，不保留 blocking ambiguity。
6. 文件具備 version、owner、status 與後續 governance mechanism。
7. Framework 已嵌入既有 backlog、Sprint、PR、test、release 與 Change Management workflow，沒有建立平行 SDLC 或中央強制模板體系。

---

## 19. Charter Statement

本專案的核心，不是讓更多人更快產生 code，而是建立一套新的工程能力：

> **讓團隊更快理解正確的問題、做出更好的 engineering decision，並用足夠 evidence 安全交付。**
