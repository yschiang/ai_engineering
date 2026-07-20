# AI Handoff — AI-Native Software Engineering Framework

> Version: v1.30
> Status: Active Working Handoff  
> Purpose: Single source of working instructions for future AI sessions  
> Governing document: `00_Project_Charter.md`  
> Method/Governance SSOT: `02_Framework.md`  
> Engineering Usage SSOT: `03_Golden_Engineering_Playbook.md`

---

## 1. Handoff Purpose

本文件用於將 **AI-Native Software Engineering Framework** 專案交給下一個 AI working session。

下一個 session 應承接已確認的定位、決策、產出結構與品質標準，不重新發明 scope，不把專案轉成單一工具教學，也不在核心 artifacts 完成前擴張到大型 prompt library。

本文件是 working-session SSOT；若與臨時 chat 討論衝突，應先以 `00_Project_Charter.md`、本文件與已確認的 `02_Framework.md` 為準，再提出需決策的差異。

---

## 2. Project Mission

建立一套部門級、Enterprise-grade、Tool-agnostic、Capability-based 的 AI-Native Software Engineering Framework。

Framework 必須同時服務兩種閱讀高度：

- **Executive / Management view**：Division Head、CIO、Department Head、Managers 能理解 strategic value、governance、risk 與 adoption outcome。
- **Engineering view**：Engineer、Senior、Tech Lead、Architect 能直接用於 requirement、design、implementation、review、testing、release 與 operation。

品質定位接近 McKinsey／BCG 等級的邏輯與表達，但內容必須是可執行的 engineering operating model。

---

## 3. Non-Negotiable Positioning

### 3.1 Framework 是什麼

- AI-Native Software Engineering operating model。
- Golden Flow + Six Golden Questions 的單一 Engineer mental model。
- End-to-end engineering responsibility coverage；不建立第二套 formal lifecycle。
- Risk-based governance model。
- Reusable engineering capability system。
- Existing SDLC、Architecture、DevOps、SRE 與 Security practices 的增強層。
- 透過 Golden Playbook 讓 Engineer 依 Work Level、Archetype 與 Current Stage 直接選 skill、artifact 與 gate。

### 3.2 Framework 不是什麼

- Claude Code、Codex、Gemini 或其他單一工具的 manual。
- Prompt collection。
- 所有 change 都適用的重量級流程。
- AI adoption 使用率 KPI 制度。
- AI 取代 human owner 或 production decision 的機制。
- 其他 software product、RMS、S7F26 或 Recipe Schema 專案的文件。

### 3.3 Writing Constraints

- 使用 Traditional Chinese，保留必要 English engineering terms。
- 結論清楚，避免 AI 式空泛語言。
- 不為了看起來完整而增加低價值章節。
- 每個概念必須能對應 decision、practice、artifact 或 evidence。
- Universal mandatory practices 原則上每個 activity 不超過三項；額外控制由 Tier/risk 觸發。
- 不虛構 external policy、organization name、tool approval 或 management decision。

---

## 4. Confirmed Core Model and Controls

### 4.1 Golden Flow + Six Golden Questions

```text
Research → Design → Plan → Implement → Validate
```

這是 Engineer 唯一需要使用的 workflow。進入新的 work item 時，Engineer 完整回答 Six Golden Questions；進入執行後通常只更新 Current Golden Stage 與 Next Move。scope、architecture、risk 或 AI authority 改變時，再完整重判。

Six Golden Questions 是每個新 work item 的 initial routing checklist：

1. 工作記在哪裡：哪個既有 ticket、PR、design doc 或 release record 是大家共同查看的地方。
2. Work Level。
3. Archetype。
4. Current Golden Stage。
5. Control Profile。
6. Next Move：required capability、active default／approved equivalent、artifact/evidence、gate owner。

`Understand、Define、Design、Build、Verify、Release、Operate` 只作為 Framework completeness／responsibility coverage vocabulary，不構成正式 lifecycle model，也不進入 Engineer-facing supplements。

### 4.2 AI 基本功 in Every Golden Stage

```text
Understand → Challenge → Execute → Evidence
```

用途：描述每個 Golden Stage 內，人與 AI 應採用的共同工作紀律。它不是第二套 lifecycle；Training 應把它教成 AI 基本功。

Skill adoption 採 `required discipline + Golden default + approved equivalent`：新手／只會 vibe coding 的 Engineer 直接使用 Golden default；成熟 Team 只有在 Skill Registry 完成相同 capability、input/output、stop condition、gate 與 evidence mapping 後才替換。

### 4.3 Change Risk Tier

| Tier | Meaning |
|---|---|
| L0 | Local / Assistive；低影響、容易重做、無 production write |
| L1 | Standard Change；單一 component、boundary 清楚、可回復 |
| L2 | Significant Change；跨 component/contract/data/architecture，需強化 design 與 verification |
| L3 | Critical Change；觸及 critical control path、不可逆 state、重大 blast radius 或 operational risk |

Tier 是 work-item/change-level classification，由最高 material risk 決定，不按 code size 或 system name 決定。Inline-critical system 不代表所有 change 都是 L3。

### 4.4 AI Execution Mode

| Mode | Meaning |
|---|---|
| E0 Observe | Read/search/analyze；不修改 artifact/system |
| E1 Propose | 產生 plan/design/draft/patch proposal；不套用 change |
| E2 Change | 在授權 workspace/repository 修改並執行 verification |
| E3 Act | 影響 external/shared/production state；需 existing authorized owner 明確核准 |

治理使用：`System Criticality × Change Risk Tier × AI Execution Mode`。

### 4.5 Universal Quality Gates

1. **Understanding Gate**：是否理解正確的系統與問題？
2. **Change Gate**：change design 是否合理、安全、可驗證？
3. **Evidence Gate**：是否有足夠 evidence 可以 release？

Gates 是共同判斷語言，不強制新增三場會議或三份表格；但每次 Pass／Conditional Pass／Rework 都必須在 existing System of Record 留下 Human Decision Record。

### 4.6 Human Accountability

AI 能協助分析、設計、實作、測試與觀察，但 accountable human 必須能回答：

- 為什麼做？
- 改了什麼？
- 如何證明正確？
- 失敗如何處理？

### 4.7 Delivery Level and Work Archetype

| Delivery Level | Meaning |
|---|---|
| P3 | Product / Program：Greenfield、Modernization/Migration、長期 platform initiative |
| P2 | Epic：跨 feature/component 的完整 capability |
| P1 | Feature：可獨立驗收、部署或控制的 bounded outcome |
| P0 | PBI / User Story：Sprint-ready、narrow but complete、可獨立驗證的 vertical slice |

P0 可為 User Story、Engineering Story / Enabler、Bug 或 time-boxed Spike。Spike 以可驗證的 evidence/decision outcome 完成，不要求 production behavior demo。

`Task / Plan Step / Commit` 位於 P0 下方的 **Execution Layer**，不是正式 Delivery Level。`Change` 也不是固定層級；OpenSpec Change 是 durable engineering artifact container，依 scope 可承載 P1 Feature 或 P0 PBI。

Work Archetype：Greenfield Product、Legacy Modernization/Migration、Standard Delivery。

### 4.8 Capability Inventory and Planning Split

Framework 可使用 Understand、Explore、Define、Design、Challenge、Plan、Implement、Verify、Release 等 capabilities；它們在 Golden Flow 內依需要被調用，不構成第二套 workflow。OpenSpec `/opsx:explore` 是 Explore capability 的 E0 reference implementation；它不建立 change artifact/code，若繼續則由 proposal/specs/design/tasks 承接。

Plan stage 的兩個問題不得混用：先判斷 P1 是否真的包含多個獨立交付成果，再判斷目前 Change／P0 如何拆成 implementation tasks。

```text
Approved P1
→ 多個獨立 outcome：to-tickets → P0 PBI / Story + Blocked by
→ 單一 bounded outcome：直接視為一個 P0
→ 已採用 OpenSpec：tasks.md 作唯一 task ledger，粗 task 在原檔展開
→ 未採用 OpenSpec：inline plan，或 writing-plans（JIT、risk/complexity triggered）
→ Execution Layer：Tasks / Plan Steps / Commits
→ TDD / Implement / Verify
```

不得先替整個 Epic 建立一份巨大 implementation plan。沒有 blocker 的 P0 形成 execution frontier；wide refactor 採 `expand → migrate batches → contract`。

#### Stage-Internal Skill Routing

OpenSpec、Superpowers、`to-tickets`、`writing-plans` 都是 Current Golden Stage 內的選擇，不是 initial routing dimension。Engineer 先完成 Six Golden Questions、定位 Current Stage 與 Next Move；客觀 engineering need 再決定 required capability，Team fit 最後決定 tool／skill implementation：

- **Research**：依第一個未知選 research、`grill-me`、`/opsx:explore` 或 debugging；一次只選一個。
- **Design**：需要跨 session／AI／Engineer 保存 durable why／what／how 時，由 OpenSpec 擁有 proposal/specs/design；否則沿用 existing design SSOT 與 Superpowers／Team equivalent。
- **Plan — delivery decomposition**：Approved P1 含多個可獨立交付 outcome 時，才使用 `to-tickets`／Team equivalent 產生 P0。
- **Plan — implementation breakdown**：已採用 OpenSpec 時使用同一份 `tasks.md`；未採用時，simple P0 inline，multi-step／high-risk／complex P0 才用 `writing-plans`。
- **Implement／Validate**：依唯一 ledger 與 execution entry 套用 TDD、debugging、review、verification；OpenSpec Change 由 `/opsx:apply` 進場。

是否採用 OpenSpec，只是 Stage 內的 artifact／execution 選擇，不形成另一個 Engineer workflow。Team 可以指定 local default，但不能降低 architecture/risk trigger、required design/test/review、Human Gate 或 evidence。OpenSpec 與 upstream Superpowers 一起使用時，必須保持單一 artifact owner、execution entry 與 task ledger；`tasks.md` 已存在時不得再呼叫 `writing-plans` 或建立另一份 plan。

### 4.9 System Design Capability

System Design 位於 Golden Design 內，不是新的 Golden Stage：

- P3 Product/Program：Required。
- P2 Epic：Required。
- P1 Feature：跨 boundary/contract/data、重大 NFR、novel architecture 或 L2–L3 時 triggered。
- P0 PBI / Story：Normally skip；觸及 architecture boundary 時升級處理。

System Design Review 是 Change Gate 的 risk-based implementation，不是第四個 Universal Quality Gate。P3/P2 architecture 使用 Product/Architecture SSOT；P1 可由 OpenSpec `design.md` 承載，避免重複文件。

### 4.10 Existing Workflow Integration

AI-Native Engineering 是既有 SDLC／delivery operating model 的 enhancement layer，不建立平行流程。

- Golden Stages 是 portable engineering decision states，不是 Department mandatory SDLC phases。
- 一個 Team activity 可承載多個 Golden Stages；一個 Golden Stage 可跨 activities／Sprints。
- Quality Gates 是 decision responsibility，不是三場新 meeting 或三份 mandatory forms。
- Artifact contract 定義 required information/evidence，不定義 mandatory file format；優先 reuse existing system of record。
- Department 擁有 minimum contract、quality bar、risk-triggered additions 與 traceability；Team 擁有 local workflow mapping、templates、tracker fields、repository instructions、technology/product/domain checks。
- E3 沿用既有 authorized owner、Release／Change Management 與 production control；AI 不能成為 production approver。
- Department 已有十個以上實際 pilot cases；下一步是 consolidation、canonical case selection 與 Case Library，不是重新要求 pilot。

---

## 5. Deliverable Architecture

`00–06` 共七個 numbered artifacts。`00–03` 是 core operating assets；`04–06` 是由 core 衍生的 supplements。Root README 負責角色導覽，Golden Skill Registry 負責 provenance／environment mapping。

| ID | Artifact | Format | Status / Purpose |
|---|---|---|---|
| 00 | `00_Project_Charter.md` | Markdown | v1.7 Baseline；單一 Golden Flow、Six Questions entry 與 Stage-internal capability selection |
| 01 | `01_AI_Handoff.md` | Markdown | v1.30；future sessions 的工作控制文件 |
| 02 | `02_Framework.md` | Markdown，25–30 頁等級 | v1.14 Baseline；Six Questions entry、Stage-internal capability selection、planning split、Durable single-ledger rule、integration 與治理 SSOT |
| 03 | `03_Golden_Engineering_Playbook.md` | Markdown | v1.12 Baseline；Six Questions → Current Stage → capability／skill／output／gate，含 OpenSpec task breakdown |
| 04 | `guides/04_Framework_Overview.md` | Diagram / Markdown | v1.12 Candidate；outer routing + Golden Flow + Stage-internal skills，待 Sponsor review |
| 05 | `guides/05_Decision_Tree.md` | Diagram / Markdown | v1.12 Candidate；compact Six Questions router + Stage-internal capability routing |
| 06 | `training/06_Training_Presentation.pptx` | PowerPoint，9 頁 | v1.16 Candidate（版本檔：`training/06_Training_Presentation_v1.16_9pages.pptx`）；P4 明示 Six Questions → Current Stage → Stage-internal skills；P6 區分 delivery outcomes 與 implementation tasks；P7 說明 Stage 內的 skill selection |

Supporting assets：`README.md` 管角色路徑與 Start Here；`reference/Golden_Skill_Registry.md` 管 skill readiness；`reference/Enforcement_E1_PR_Decision_Record.md` 提供單一 Team 可直接複製的 E1 workflow 與 example PR。Decision Tree 開頭同時擔任 quick reference，不另行維護 `07` content SSOT。

Case Library 是既有十個以上 pilots 的持續演進 evidence collection；Team-specific templates 由 Team 管理。其他 bonus items 必須有真實 adoption need，避免文件/checklist 無限制增加。

---

## 6. Current Status

### Completed

- Project Charter 已重建為正式 artifact。
- AI Handoff 已重建為正式 artifact。
- `00_Project_Charter.md` v1.7 已將 Golden Flow 保留為唯一 Engineer workflow，並區分 Six Questions initial routing 與執行中的 Stage／Next Move refresh。
- `02_Framework.md` v1.14 Baseline 已將 Six Golden Questions 固定為 initial routing，並明定 skills/tools 只能在 Current Stage 內選擇；Plan 分開 delivery decomposition 與 implementation breakdown。
- `03_Golden_Engineering_Playbook.md` v1.12 Baseline 已將 Engineer 入口改為 Six Golden Questions → Current Stage → Stage-internal capability；OpenSpec `tasks.md` 保留 implementation breakdown、single ledger、JIT nested breakdown 與 `/opsx:update` 邊界。
- `README.md` 已建立 Start Here、artifact guide 與 role-based reading paths；Engineer 以 `03` 為必要 execution SSOT，第一次接觸可選讀 `04`，routing ambiguity 才查 `05`。
- `reference/Golden_Skill_Registry.md` 已把 manual `system-research`／`codebase-research` 定為 active capability defaults；`understand-anything` 保持 candidate equivalent，不阻塞 rollout。
- `reference/Enforcement_E1_PR_Decision_Record.md` 已定義只先 rollout Human Decision Record on PR；提供 copyable workflow／example PR，其他 detection 維持未啟用。
- `guides/04_Framework_Overview.md` v1.12 Candidate 與 `guides/05_Decision_Tree.md` v1.12 Candidate 已同步 Six Questions entry、Golden Flow、Stage-internal capability selection、conditional P1 slicing，以及 OpenSpec `tasks.md`／Superpowers TDD 的實際接點；`05` 開頭同時擔任 compact quick reference。
- `reference/Golden_Skill_Registry.md` 已新增 OpenSpec capability mapping 與 OpenSpec Change reference sequence；community `superpowers-bridge` 保持 candidate，不作 Department default。
- `training/06_Training_Presentation_v1.16_9pages.pptx` 共 9 頁；P4 明示 initial routing 是 Six Questions，skill selection 位於 Current Stage 內；P6 將 Plan 拆成 P1 → P0 delivery outcomes 與 Change／P0 → implementation tasks，OpenSpec `tasks.md` 是採用 OpenSpec 時的唯一 implementation ledger；P7 將 OpenSpec、Superpowers、`to-tickets`、`writing-plans` 放回各自 Stage。P8 的 8 週 → 6 週仍是需由 pilots 校準的 illustration。已完成全頁 render、changed-slide inspection、overflow 與 template fidelity QA。

### Framework 已涵蓋

- Executive Summary、Purpose、Design Principles。
- Golden Flow + Six Golden Questions；每個 Stage 的 AI 基本功；E0–E3 AI Execution Mode。
- `System Criticality × L0–L3 Change Risk Tier × AI Execution Mode` Control Profile。
- Understand、Define、Design、Build、Verify、Release、Operate responsibility coverage reference appendix；不是 formal lifecycle model 或 Engineer path。
- Role Expectations。
- Core Use Cases。
- Artifact Model 與 Repository/I/O Blueprint。
- P3–P0 Delivery Level、Work Archetype 與 Golden capability mapping。
- System Design capability、trigger、System Design Pack、Change Gate review 與 architecture/OpenSpec SSOT boundary。
- P1 → P0 delivery slicing、P0 → Execution Layer JIT planning、dependency frontier 與 tracker reference mapping。
- Existing workflow integration、non-normative common SDLC reference mapping、Gate placement、artifact placement、Agile/Sprint DoR/DoD、E3 existing authorization。
- Department minimum contract／quality bar 與 Team-owned workflow/templates governance。
- Existing 10+ pilot consolidation、canonical cases 與 Case Library evidence model。
- Reusable Working Patterns。
- Three Quality Gates。
- Definition of Done。
- Metrics、Adoption Model、Anti-patterns、Decision Guide、Templates 與 Governance。

### Next Required Work

1. Consolidate 既有十個以上 pilot cases，依 Work Level、Archetype、Golden Stage、AI 基本功的實際運用、Golden default/equivalent skill、Risk Tier、Execution Mode、artifacts/evidence、outcome、failure learning mapping；選 3–5 canonical cases，其餘進 Case Library。
2. 請每個 Team 建立輕量 local workflow adapter：existing activities／systems of record → Golden questions／Gates → artifact placement／decision owner；Team 自主管理 templates，不由 Department 集中設計。
3. Sponsor/Engineering 確認 `04` v1.12、`05` v1.12 與 Training v1.16 的 Six Questions entry、Golden Flow、Stage-internal capability selection、OpenSpec task breakdown、P1 Feature Golden Path、active defaults、human judgment × AI execution notes、三個 target outcomes、8 週 → 6 週 assumptions 與 usability。
4. 若要將第三方 Research skill 升為 approved installable implementation，再完成 source/license review、vendor/pin 與逐 environment verification；manual defaults 在此之前持續可用。

---

## 7. Repository Blueprint

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

### I/O Rules

- 只在有實際內容時建立 supporting directory；repository blueprint 不預先列空資料夾。
- `guides/`：可自行閱讀、按需查詢的 overview 與 routing reference。
- `training/`：實際存在的 PowerPoint、assets 與 rendered review artifacts。
- `reference/`：影響判斷但不是 core method 的 source／mapping reference。

---

## 8. Source of Truth Hierarchy

| Priority | Artifact | Responsibility |
|---:|---|---|
| 1 | `00_Project_Charter.md` | Why、scope、non-goals、success criteria |
| 2 | `01_AI_Handoff.md` | Working rules、current status、next actions |
| 3 | `02_Framework.md` | Golden model、responsibility coverage、Tier、roles、gates、practices |
| 4 | `03_Golden_Engineering_Playbook.md` | Delivery Level、Archetype、skill → artifact → gate execution mapping |
| 5 | `reference/Golden_Skill_Registry.md` | Skill implementation source、environment、installation、invocation、status、fallback |
| 6 | `04–06` | 由 Framework + Playbook 衍生的 overview、routing 與 training supplements |
| 7 | `README.md` | 角色導覽與 Start Here；不新增 method |
| 8 | Working notes / chat | 暫時 context，不得凌駕正式 artifacts |

若衍生 artifact 與 Framework 不一致，優先修正衍生 artifact。若發現 Framework 與 Charter 衝突，必須明確提出 decision，不得自行改變 project intent。

---

## 9. Working Session Protocol

### Step 1 — Read Before Producing

每個新 session 先讀：

1. `00_Project_Charter.md`
2. `01_AI_Handoff.md`
3. `02_Framework.md`
4. 與工程流程或 supplements 相關時讀 `03_Golden_Engineering_Playbook.md`

### Step 2 — Restate the Assignment

開始前用精簡方式確認：

- 本輪 goal。
- Inputs/SSOT。
- Expected artifact。
- Constraints。
- Definition of Done。

不需要重新詢問 Charter 已經決定的事項。

### Step 3 — Inspect for Consistency

確認：

- Terminology 是否一致。
- Capability model、Tier、gates 是否被正確使用。
- 是否與既有 artifacts 重複或衝突。
- 是否不必要地增加 mandatory controls。

### Step 4 — Produce the Artifact

- 直接建立正式檔案，不只在 chat 中貼文字。
- 使用約定 filename 與 directory。
- 需要圖形時使用適合後續簡報與文件重用的結構。
- PowerPoint 必須是 `.pptx`，不是 Markdown outline。

### Step 5 — Verify

至少檢查：

- Completeness。
- Internal consistency。
- Executive clarity。
- Engineering usability。
- Formatting/rendering quality。
- Artifact 已可被下一個 session 接手。

### Step 6 — Update Handoff

若完成重大 deliverable 或做出核心 decision，更新：

- Current Status。
- Confirmed Decisions。
- Next Required Work。
- Open Issues。

---

## 10. Quality Standards

### 10.1 Content Quality

- 先給 conclusion，再給 supporting logic。
- 每個 section 必須回答明確問題。
- 內容 MECE，避免同一概念在多處以不同名稱重複。
- Principle 必須能轉成 action 或 decision。
- Practice 必須說清楚 trigger、owner 或 evidence。

### 10.2 Executive Quality

- Division Head / CIO 能在短時間理解 Why、Model、Risk、Outcome。
- 不使用過多 AI buzzwords。
- 不以工具功能取代 strategic narrative。
- 對 productivity、quality、reliability 保持 balanced view。

### 10.3 Engineering Quality

- 適用 production-critical systems。
- 涵蓋 failure、recovery、observability、testability 與 operability。
- 不以「human review」作為沒有具體方法的萬用答案。
- Evidence strength 與 Tier/risk 相稱。
- 能被 ticket、PR、design review 與 release process 承載。

### 10.4 Visual Quality

- 每個 diagram 只表達一個主要 relationship。
- Overview 不塞滿全部細節。
- Decision Tree 的每個 decision 必須能導向 action。
- Training slide 原則上一頁一個 message。
- Decision Tree 的 opening router 必須可在一頁內掃描使用；detailed routing 可在後續 sections 展開。

---

## 11. Framework Review Record

`02_Framework.md` v0.9 已完成 strict review，verdict 為 **7.6/10，Ready after targeted major revision**。核准後以 Minimal Patch 關閉：

1. 新增 E0–E3 AI Execution Mode。
2. 將 Project Tier 修正為 work-item/change-level Change Risk Tier，並與 System Criticality 分離。
3. 將多組 Mandatory Practices 改為 Core Questions，只保留三項 Universal Controls。
4. 將 Evidence Hierarchy 修正為 Evidence Portfolio。
5. 壓縮 Use Cases、Repository、Anti-patterns、Templates 等重複內容，並新增 L1/L3 worked examples。

`02_Framework.md` v1.2–v1.3 後續加入：

6. P3–P0 Delivery Level 與 Greenfield / Modernization-Migration / Standard Archetype。
7. 早期版本加入 Understand／Explore／Define 等 capability inventory；v1.6 已明確改為 Golden Flow 內的可調用能力，不構成第二套 workflow。
8. 明確由 `03_Golden_Engineering_Playbook.md` 管理 OpenSpec、Superpowers 與 Department skills 的 execution mapping。

`03_Golden_Engineering_Playbook.md` v1.0 strict review verdict 為 **8.0/10，Ready after targeted revision**。Approved Minimal Patch 已在 v1.1 關閉：

9. 將 System Design 提升為 Design stage 內的明確 capability，不新增 lifecycle stage。
10. 定義 P3/P2 required、P1 risk-triggered、P0 normally skip。
11. 明確定義 System Design engineering activity、System Design Pack 與 System Design Review；System Design 不是 skill，也沒有固定 tool dependency。
12. 明確 System Design Review 屬於 Change Gate，並分開 P3/P2 Architecture SSOT 與 P1 OpenSpec `design.md`。

`02_Framework.md` v1.4 與 `03_Golden_Engineering_Playbook.md` v1.2 完成 hierarchy semantic correction：

13. P0 改為 PBI/User Story vertical slice；Task/Plan Step/Commit 移至 Execution Layer。
14. OpenSpec Change 改為 P1/P0 scope-dependent durable artifact container，不再是固定 Work Level。
15. `to-tickets` 負責 P1 → P0；`writing-plans` 僅對單一即將執行的 P0 做 JIT implementation planning。
16. 加入 blocker frontier、expand/migrate/contract 與 Azure DevOps/GitLab reference mapping；Golden Flow、三個 gates 與 System Design trigger 不變。

`04_Framework_Overview.md` v1.1 與 `05_Decision_Tree.md` v1.0 combined review verdict 為 **8.4/10，Ready after targeted revision**。Approved patch 已在 04 v1.2 / 05 v1.1 關閉：

17. 05 將 compact Current Stage router 移到 60-second entry。
18. 05 澄清 P1 Feature outcome 與 P0 smallest Sprint tracer bullet，並加入 Release/Operate overlay。
19. 05 將 OpenSpec `Continue` 改成 explicit next action，Fast Routes/Tracker 移至 appendices。
20. 04 壓縮 System Design、capability、gate 與 tracker detail，保留 one-page decision model。
21. Feature、Bug、Modernization routes 均包含不同 skills、artifacts、controls 與 closure/release path。

`05_Decision_Tree.md` v1.2 加入 department-use Golden Matrix：

22. 以 Golden Stage 為 rows、P3–P0 為 columns，每格直接呈現 `required activity／supporting skill → minimum output`。
23. 明確區分 P3/P2 delivery decomposition、P1 `to-tickets` 與 P0 JIT `writing-plans`。
24. Matrix output 作為下一 stage handoff，可存在既有 ticket/OpenSpec/ADR/PR，不新增 mandatory document。

`06_Training_Presentation.pptx` v1.0 Candidate 將 04/05 轉為 Department training storyline：

25. 10 頁依序回答 Why、Operating Model、Work Level、Golden Matrix、planning split、capability responsibility、controls/gates、common routes、roles 與 adoption mission。
26. Golden Matrix 是 training 中央操作面：先選 P3–P0 column，再找 Current Stage row，cell 直接給 `activity／supporting skill → output`。
27. New Feature、Bug、Modernization routes 展示相同 Golden Flow 如何依 context 使用不同 rigor 與 evidence。
28. PowerPoint 已完成 CJK font rendering、逐頁 visual inspection 與 overflow validation；沒有新增 lifecycle stage 或 universal gate。

`06_Training_Presentation.pptx` v1.1 Baseline Candidate 完成 approved Minimal Patch：

29. Golden Matrix 與 capability operational text 以 16pt room-readable body copy 呈現，透過縮短 cell wording 避免增加資訊密度。
30. OpenSpec command chain 明確分為 optional E0 `/opsx:explore`、durable `/opsx:propose` 或 `/opsx:new + /opsx:continue`、execute/close `/opsx:apply → /opsx:verify → /opsx:sync → /opsx:archive`。
31. Evidence Gate 後的 shared/production change 明確交給 existing release process，使用 E3 authorization、observation 與 recovery control。
32. Team Mission 指定 Tech Lead 在 Sprint Review 檢查 routing evidence 與 friction；全 10 頁完成 CJK rendering、逐頁 visual inspection 與 overflow validation。

`05_Decision_Tree.md` v1.3 與 `06_Training_Presentation.pptx` v1.2 完成 Golden Matrix semantic correction：

33. Matrix 明確定位為 default routing：Archetype 改變起始 evidence／validation focus，Control Profile 改變 rigor／evidence depth；兩者不新增 stage 或 Matrix 軸。
34. P3 Research 同時涵蓋 Greenfield Product Brief 與 Modernization As-Is Brief；P0 Research 顯示 research/debug 分流。
35. Plan row 恢復正式分工：P3/P2 delivery decomposition、P1 `to-tickets → P0 slices + blockers`、P0 inline/JIT plan → Execution Layer tasks；無 blocker 即 execution frontier。
36. Implement row 明確 P3/P2 遞迴執行 child flows，P1 執行 frontier P0s；Validate 才做 evidence rollup/acceptance。System Design trigger footnote 保持 P3/P2 required、P1 risk-triggered、P0 normally skip。
37. Training deck v1.2 全 10 頁完成 CJK rendering、逐頁 visual inspection 與 overflow validation；沒有增加 stage、gate 或 mandatory artifact。

`06_Training_Presentation.pptx` v1.3 新增 AI Engineering target outcome comparison：

38. 在三條常見路徑之後、adoption action 之前新增一頁，回答 Golden Playbook 預期改變的 engineering outcome，而不是新增另一套 workflow。
39. 以兩條相同 total effort = 100 的 continuous stacked bars 呈現 effort reallocation：As-Is 偏重 implementation；AI Engineering target 增加 system-wide Research、explicit Design/Plan 與 broader Validate，implementation 由 55 降至 8（約 1/7，位於 1/5–1/10 目標範圍）。
40. Outcome 收斂為 design quality 提升、implementation effort 降低 80–90%、patches/rework 明顯下降；所有數值均標示為 target illustration，需由 pilot actual baseline 校準。
41. Training deck v1.3 共 11 頁；完成 CJK rendering、逐頁 visual inspection、overflow test、template fidelity 與 empty-placeholder QA。

`06_Training_Presentation.pptx` v1.4 將 target outcome 修正為 calendar cycle-time illustration：

42. 代表性 Feature 由 As-Is 8.0 週修正為 AI Engineering target 5.5 週，對外以 5–6 週／約 3 個 two-week Sprints 表達；總 calendar time 約下降 31%。
43. Stage allocation 為 Research `0.75 → 0.75` 週、Design `0.5 → 1.0` 週、Plan `0.25 → 0.25` 週、Implement `5.5 → 2.25` 週、Validate `1.0 → 1.25` 週；目的不是壓縮 design/test，而是以更完整的前置決策與 evidence 減少 coding 與 rework。
44. Continuous stacked bars 改為 raster PNG 嵌入 PowerPoint，避免 PowerPoint／LibreOffice chart engine 差異；同時輸出完整 Slide 10 PNG 與可重用 bar asset。
45. Training deck v1.4 共 11 頁；完成 CJK rendering、逐頁 visual inspection、overflow test、template fidelity、image-vs-chart 與 empty-placeholder QA，沒有新增 lifecycle stage、gate 或 mandatory artifact。

`06_Training_Presentation.pptx` v1.5 將 target allocation 定稿為三個 two-week blocks：

46. 代表性 Feature 由 As-Is 8 週／4 Sprints 縮短為 AI Engineering target 6 週／3 Sprints；總 calendar time 約下降 25%。
47. Stage allocation 為 Research `0.75 → 0.75` 週、Design `0.5 → 1.0` 週、Plan `0.25 → 0.25` 週、Implement `5.5 → 2.0` 週、Validate `1.0 → 2.0` 週。
48. 新配置形成直覺的 `Research + Design + Plan = 2 週`、`Implement = 2 週`、`Validate = 2 週`；Implementation stage 約下降 64%，Validate 明確包含 TDD、staging 與 production readiness，以較少 patch/rework 完成交付。
49. Training deck v1.5 共 11 頁；chart 仍以 raster PNG 嵌入，並完成 CJK rendering、逐頁 visual inspection、overflow test、template fidelity、image-vs-chart 與 empty-placeholder QA。

`00` v1.4、`02` v1.5、`03` v1.3、`05` v1.4 與 `06` v1.6 完成 existing SDLC integration correction：

50. Framework 明確定位為 existing SDLC／delivery operating model 的 enhancement layer，不建立平行 SDLC；原有 ownership、approval、release 與 production accountability 不變。
51. Golden Stages 保留 `Research → Design → Plan → Implement → Validate`，但改以 portable engineering decision states 定義；common SDLC activities 只作 non-normative Appendix reference，Team 擁有 local mapping。
52. Three Gates 明確 mapping 到 refinement/design/PR/test/release 等 existing touchpoints；Gate 是 decision responsibility，不是新 meeting/document。L0/L1 可 inline，L2/L3 才依 risk 提高 formality。
53. Artifact requirement 改為 information/evidence contract；優先 reuse existing tracker、OpenSpec、design/RFC/ADR、PR、test、release/change record、dashboard/runbook，reference rather than copy。
54. Department 擁有 minimum artifact contract、quality bar、risk-triggered additions 與 traceability；Team 擁有 templates、tracker fields、repository instructions、technology/product/domain checks。
55. Agile/Sprint integration 明確 P0 DoR/DoD，且 Sprint boundary 不等於 Golden Stage boundary；Research、Design、Validate 可在同 Sprint、Spike、Feature-level 或 cross-Sprint 出現。
56. E3 沿用 Existing Change Approval 與 authorized production owner；AI 不能成為 approver。流程為 `Verified Change → Release Readiness → Existing Change Approval → Explicit E3 Authorization → Execute → Observe → Validate → Recover/Rollback`。
57. Department 已有十個以上 pilots 作為 evidence base；後續工作是 consolidation、3–5 canonical cases 與 Case Library，不再建立新 pilot gate。
58. Training deck v1.6 共 12 頁；新增 existing-workflow enhancement slide，引用現有 pilot evidence；最後一頁改為 existing-workflow-first／Team Adapter。完成 12-slide CJK render、逐頁 visual inspection、overflow、page marker、template fidelity 與 placeholder QA。

`00` v1.5、`01` v1.16、`02` v1.6、`03` v1.4、`04` v1.4、`05` v1.5 與 `06` v1.7 完成 Engineer mental-model 與 skill-adoption correction：

59. Golden Flow `Research → Design → Plan → Implement → Validate` 成為唯一 Engineer workflow；Six Golden Questions 成為定位與開始工作的唯一入口。
60. `Understand → Challenge → Execute → Evidence` 改為每個 Golden Stage 都要練的 AI 基本功，不再呈現為另一個 lifecycle／work loop。
61. Understand、Define、Design、Build、Verify、Release、Operate 只保留為 Framework responsibility coverage vocabulary；不命名為 formal model，不進入 Engineer-facing supplements。
62. Skill governance 改為 `required discipline + Golden default + approved equivalent`：新手／只會 vibe coding 的 Engineer 直接採 defaults；Team 替換前必須完成 capability、input/output、stop condition、gate 與 evidence 等價 mapping。
63. Golden Matrix 每格明確使用 required activity／supporting skill → minimum output；Decision Tree 以 Six Questions 導向 next move，不再要求 Engineer 同時記住兩套心智模型。
64. Training deck v1.7 共 12 頁；slide 3 將 AI Work Loop 改為 AI 基本功，slide 4 明示 single workflow + Six Questions，slides 6/8 強化 Golden defaults，slide 12 直接列出六個啟動問題。完成全頁 CJK render、逐頁 visual inspection、overflow、template fidelity 與 empty-placeholder QA。

`01` v1.17 與 `06` v1.8 完成 Feature-first presentation condensation：

65. Training deck 以 P1 Feature 作為唯一 teaching example；Work Level 只決定 depth，Task 仍位於 P0 下方 Execution Layer。
66. 原 slides 7–9 的 stage matrix、skill policy 與 risk detail，以及原 slide 10 的 walkthrough，合併成單一 Engineer operational takeaway：先把問題弄對、再把交付切小、最後用證據完成。
67. 合併頁明示 Golden Flow 決定 next step、Golden Default skill 決定 how、risk 只改變 rigor 不改變 route；避免工程師看完仍不知道下一步。
68. Plan 頁直接呈現 `Approved P1 → to-tickets → P0 vertical slices / Blocked by → triggered writing-plans → implementation tasks`。
69. Outcome 頁明示總時間 `8 → 6 weeks (-25%)`；final deck 共 9 頁，完成全頁 CJK render、逐頁 visual inspection、overflow、template fidelity、page marker 與 empty-placeholder QA。

`01` v1.18 與 `06` v1.9 完成 concrete problem opening 與 target allocation refinement：

70. P2 將抽象的 Why 改成工程師可直接理解的兩個問題：small change 與跨 Repo Feature 不能只用同一個 prompt/session；AI 讓 coding 變快，也會讓 bad code、patch 與技術債累積更快，因此 work 越大，Research／Design／Plan／Validate 必須越深。
71. P3 明確說明本次建立的是 durable AI Development Workflow：models 會持續變強，但 workflow、ownership 與 evidence 必須持久；同一 Golden Flow 適用 P3→P0，只改變深度，並提供由既有 10+ pilots 淬煉的 Golden default skills／approved-equivalent adoption path。
72. P8 的 8 週 → 6 週 illustrative target allocation 定為 Research `0.75 → 0.75`、Design `0.5 → 1.5`、Plan `0.25 → 0.25`、Implement `5.5 → 1.5`、Validate `1.0 → 2.0` 週；Design 與 Implement 各 1.5 週，Implementation 約下降 73%，並以更完整 FR／NFR／failure modes 與 TDD／staging／readiness 降低 patch/rework。
73. Training deck v1.9 維持 9 頁；P2 使用使用者提供、源自 Dex Horthy《No Vibes Allowed》的 problem-size/context-engineering 圖示概念，P8 保持 raster chart。完成全頁 CJK render、逐頁 full-size inspection、overflow、template fidelity、page marker、slide count 與 empty-placeholder QA。

`01` v1.19 與 `06` v1.10 完成 problem-only opening simplification：

74. P2 改為左右兩個大型問題區塊，直接使用 problem-size/context-engineering 與 bad-research/bad-plan amplification 兩張圖；不再在此頁先教 solution taxonomy。
75. P2 移除 Small Change／P1 Feature／P2-P3 底部分類與方法 footer，只保留兩句工程師可直接理解的問題：不同大小的工作需要不同 workflow depth；coding 變快變便宜會更快放大前段錯誤、bad code 與技術債。
76. Training deck v1.10 維持 9 頁；P1 僅更新版本標記、P2 完成上述重構，其餘 approved narrative 不變。完成全頁 CJK render、逐頁 full-size inspection、overflow、template fidelity、page marker、slide count 與 empty-placeholder QA。

`00` v1.7、`01` v1.20、`02` v1.8、`03` v1.6、`04` v1.6、`05` v1.7 與 `06` v1.11 完成 simplicity/effectiveness correction：

77. Engineer routing 區分兩個 cadence：新 work item 完整回答 Six Golden Questions；執行中通常只更新 Current Stage／Next Move，scope、architecture、risk 或 AI authority 改變時再完整重判。
78. Sections 6–12 降為 responsibility reference appendix；Framework Change Policy 改為 canonical ownership + impact-based synchronization。Tracker table 與 E3 chain 只留 canonical home，Playbook／Decision Tree 改用 link；Overview/router 只保留必要 guardrail。
79. Research rollout gap 已關閉：manual `system-research`／`codebase-research` 是不需安裝的 active capability defaults；`understand-anything` 與第三方 codebase skill 保持 candidate implementation，核准前不得冒充 active default。
80. Training deck P4/P9 同步 initial vs continue routing；P7 使用 read-only codebase research。P8 底部改為三個 target outcomes：Collaboration ↑（documented decisions + shared evidence/handoff）、Lead Time ↓（faster implementation + fewer rework loops）、Change Failure Rate ↓（design/code/test quality + release readiness）。
81. Training deck v1.11 維持 9 頁與既有 template／chart；完成 CJK render、逐頁 full-size inspection、overflow、template fidelity、page marker、slide count、compressed-data 與 empty-placeholder QA。

`01` v1.23、`02` v1.11、`03` v1.8、`04` v1.9 與 `05` v1.9 完成 Responsibility Ownership correction：

82. Golden Flow 不變；新增 Direction／roles、Spec-Driven Development、Engineering discipline、Execution orchestration、Evidence／approval 五項責任分工，避免再以 framework 品牌推導 lifecycle。
83. Canonical default 定為 OpenSpec 擁有 Spec-Driven Development/change traceability；Superpowers 提供 TDD-centered engineering disciplines。兩者都可跨 Design／Plan／Implement／Validate，不以假分工隱藏 overlap。
84. Fast Delivery 可直接使用完整 Superpowers／Team equivalent；Durable Change 由 OpenSpec 擁有 proposal/specs/design/tasks 與 `/opsx:apply` entry，再選用不重複 artifact 的 TDD/debugging/review/verification disciplines；Discovery First 只處理第一個未知。
85. Mixed mode 固定單一 spec/design owner、plan/task ledger 與 execution entry；community bridge 只列 candidate，未核准前不建立兩份 design/plan SSOT。
86. `reference/Flow_Responsibility_Update_Proposal.md` 保留為本輪 review basis；`reference/Golden_Skill_Registry.md` 已補 OpenSpec commands 與 Durable Change reference sequence。

`01` v1.24、`03` v1.9、`04` v1.10 與 `05` v1.10 完成 Engineer-path simplification：

87. Historical v1.9：Engineer start path 曾收斂為 Fast Delivery／Complex-Durable Change 兩條 route；**此入口已由 decision 101 取代**，兩者只保留為 Stage-internal profiles。
88. Historical v1.9：Discovery First 曾作為 pre-route 表達；**decision 101 改由 Six Golden Questions／Current Stage 統一定位第一個未知**。
89. 新增可複製的 apply-session execution contract 與 Spec-to-TDD handoff table；明定 `/opsx:apply` 選擇/追蹤 task，`test-driven-development` 執行 RED → GREEN → REFACTOR，spec/scope 改變則停下更新 OpenSpec 並重新取得 Human decision。

`01` v1.25、`02` v1.12 與 `03` v1.10 完成 Durable single-ledger correction：

90. Durable Change 的 OpenSpec `tasks.md` 是唯一 task ledger；`/opsx:apply` 依它取 task、執行、打勾與交接，禁止使用 `writing-plans` 或另建 ledger。
91. 粗 task 在 `/opsx:apply` 當下直接於 `tasks.md` 展開成帶 exact paths、failing test 與 green criterion 的巢狀子項；Engineer checkpoint 不是新 Gate。
92. 邊界判準固定為「只長出子項是 JIT；改變做法是 design change」；後者使用 `/opsx:update`，並依 scope/risk 判斷 Change Gate。

`01` v1.26 與 `06` v1.12 完成 Training single-ledger correction：

93. Training P6 將 P0 Implement 收斂為兩條路：Fast Delivery 使用 Superpowers；Durable Change 由 OpenSpec `tasks.md` 作唯一 ledger，`/opsx:apply` 接 Superpowers per-task TDD。
94. Training P6 用單一例子呈現粗 task 原檔 JIT 展開，並保留「只長子項是 JIT；改變做法走 `/opsx:update`」邊界；不新增 lifecycle、Gate 或第二份 plan。
95. Training P7 同步 Fast／Durable handoff；deck 維持 9 頁與既有 template，完成 CJK render、逐頁 full-size inspection、overflow、template fidelity、page marker、slide count 與 empty-placeholder QA。

`01` v1.27 與 `06` v1.13 完成 Training human-leverage clarification：

96. Training P2 說明 coding 可能先被 AI 自動化，而 software engineering 的價值移向問題定義、設計判斷與責任；不把此趨勢寫成固定時間表。
97. Training P3/P9 明確表達：AI 執行比例愈高，人的少數關鍵判斷愈被放大；Engineer 仍負責六題、design trade-off、evidence 與 approval。
98. Training P8 以 Human judgment × AI execution 解釋 productivity leverage；8 週 → 6 週仍標示為 illustrative target、以 pilots 校準。Deck 維持 9 頁與既有 template，完成 CJK render、逐頁 full-size inspection、overflow 與 template fidelity QA。

`01` v1.28 與 `06` v1.14 完成 Training P3/P4 de-duplication：

99. P3 不再重複 Golden Flow，改以 Human Judgment／Durable Workflow／AI Execution 三欄說明責任分工：人決定方向，workflow 保存共識與 evidence，AI 加速執行。
100. P4 保持唯一的 Golden Flow／Stage／Next Move 操作頁；P3 回答「誰負責什麼」，P4 回答「工作怎麼走」。Deck 維持 9 頁，完成全頁 CJK render、overflow 與 template fidelity QA。

`01` v1.29、`02` v1.14、`03` v1.12、`04` v1.12 與 `05` v1.12 完成 Engineer-entry correction：

101. Six Golden Questions 是 initial routing；Golden Flow 定位 Current Stage；OpenSpec、Superpowers、`to-tickets`、`writing-plans` 只在 Stage 內選擇。Plan 分成 P1→P0 delivery decomposition 與 Change／P0→tasks implementation breakdown；OpenSpec `tasks.md` 保留原檔 JIT breakdown 與 single-ledger ownership。

`01` v1.30 與 `06` v1.16 完成 Training synchronization：

102. P4 將操作順序明示為 Six Questions → Current Stage → Stage-internal capability／skill／output／gate；P6 將 delivery outcomes 與 implementation tasks 分開，採用 OpenSpec 時只使用 `tasks.md` 作 implementation ledger；P7 不再把 Fast／Durable 或工具選擇畫成外層入口。Deck 維持 9 頁，完成全頁 render、changed-slide inspection、overflow 與 template fidelity QA。

後續若變更核心模型，仍應使用相同 review format：Executive Verdict、Score、Must-Fix、Should-Fix、Remove/Merge、Missing Decisions、Minimal Patch Plan。

---

## 12. Definition of Done by Artifact

### 00 Project Charter

- Why、scope、non-goals、deliverables、success criteria 清楚。
- 能防止專案漂移。

### 01 AI Handoff

- 下一個 session 不依賴舊 chat 即可工作。
- Current status、SSOT、next action 與 constraints 清楚。

### 02 Framework

- 具備 25–30 頁等級的完整方法論。
- 模型一致且可執行。
- 通過 executive、engineering、risk 與 minimality review。

### 03 Golden Engineering Playbook

- Engineer 能在 60 秒內完成 Six Questions：確認工作記在哪裡、Work Level、Archetype、Current Stage、Control Profile 與 Next Move。
- P3 Greenfield、P3 Modernization/Migration、P2 Epic、P1 Feature、P0 PBI/User Story（含 Story/Enabler/Bug/Spike）都有 flow。
- 每個 stage 明確對應 skill、artifact 與 human gate。
- Research manual capability defaults 可直接執行；其他 approved defaults／Team equivalents 有明確 mapping contract，candidate skill 不阻塞 rollout。
- 每個 stage 明確說明 typical existing activity、artifact location、decision owner 與是否需 additional process；local mapping 由 Team 擁有。
- Responsibility Ownership 清楚：OpenSpec 擁有 durable Spec-Driven Development/change traceability；Superpowers 提供 TDD-centered engineering disciplines。混用時只有一個 spec/design/tasks owner、execution entry 與 task ledger。
- System Design 在 P3/P2 與 triggered P1 可被直接選到；P0 不被強制套用。
- System Design Review 是 Change Gate implementation，沒有新增 universal gate。

### 04 Framework Overview

- 一頁看懂 Golden Flow、日常必要判斷、triggered routing context、AI 基本功、gates 與 outcome。
- 明確呈現 P3 → P2 → P1 → P0 → Execution Layer，以及 conditional `to-tickets`、OpenSpec `tasks.md`／non-OpenSpec per-P0 JIT `writing-plans` 分工。
- 不把 responsibility coverage 或 AI 基本功畫成第二套 Engineer workflow。
- 不依賴長篇文字才能理解基本關係。

### 05 Decision Tree

- 能從 change context 判定 Tier。
- 能在 60 秒內由 existing work location 與 largest unknown/risk 導向 next activity／supporting capability、artifact placement 與 gate；只有會改變決策時才補詳細 taxonomy。
- 保留 conditional P1 → multiple P0 `to-tickets`、OpenSpec `tasks.md`／non-OpenSpec per-P0 JIT `writing-plans`、Task as Execution Layer 與 OpenSpec P1/P0 scope rule。
- 能導向必要 understanding、design、verification 與 release controls。
- 不將每條路徑導向相同流程。

### 06 Training Presentation

- 8–12 頁 PowerPoint；以最短可教會 Engineer 的 storyline 為準。
- Storyline 清楚，適合 Department Meeting 或 training。
- 包含 Why now、existing workflow enhancement、model、how to work、roles、Team adapter/call to action。

### Root README + Golden Skill Registry

- README 能依角色說明每份 artifact 的用途、使用時機、閱讀順序與 SSOT。
- Engineer 路徑以 `03` 的對應工作章節為主；`04` 是 optional visual summary，`05` 只在 routing ambiguity 時按需查閱。
- Skill Registry 能區分 active manual default、approved/candidate implementation，並追溯 source、environment、invocation、expected output、stop condition 與 fallback。
- `05` 開頭同時擔任 quick reference，不另行建立重複的 `07` content SSOT。

---

## 13. Do Not Do

後續 AI session 不得：

- 重新命名或重定義專案，除非 Sponsor 明確要求。
- 把 Framework 改成 Claude Code/Codex 教學。
- 將 prompt library 提升為主要交付物。
- 未讀 SSOT 就直接產生衍生 artifact。
- 為了完整性加入大量 generic SDLC content。
- 建立另一套平行 AI SDLC，或把 common Intake／Refine／Build／Release table 當成所有 Team 必須採用的標準流程。
- 把 responsibility coverage、capability inventory 或 AI 基本功包裝成第二套 Engineer workflow。
- 把 Golden Stages 一對一綁定固定 SDLC phases；Team workflow 與 Stage mapping 必須保持彈性。
- 把所有 practices 設為 mandatory。
- 把 active defaults 降成可忽略的建議清單；Research 直接採 manual contract，其他 capability 在未完成 approved-equivalent mapping 前採 approved defaults。
- 用更多文件解決 ownership 或 judgment 問題。
- 由 Department 集中設計所有 Team templates、tracker fields、repository instructions 或 technology/product checklists。
- 忽略既有十個以上 pilots，重新要求 Team 執行 pilot 才能證明 Framework。
- 無限制增加 framework 文件、meeting、checklist 或 template。
- 只產生 chat 文字，不建立實際 artifact。
- 將 Training Presentation 產生成 Markdown 代替 `.pptx`。
- 未 review Framework 就在衍生 artifacts 中新增核心概念。
- 把 presentation、tree 或 quick reference 當成 framework 本體；它們是 supplements。
- 強制每個 P0 使用完整 OpenSpec Change，或讓 OpenSpec 與 skill workflow 產生雙份 plan。
- 把 Task 當成 P0 Work Level，或把 OpenSpec Change 綁死在 P0/P1 任一固定層級。
- 對整個 Epic 預先產生巨大 implementation plan；應先拆 Features/P0，再做 per-P0 JIT planning。
- 把 System Design 變成每個 P0/P1 work item 的 mandatory ceremony，或新增第四個 universal gate。
- 複製 P3/P2 Architecture SSOT 到 OpenSpec change folder。
- 混入其他 project 的 RMS、Recipe Parser、S7F26 或 schema onboarding content。

---

## 14. Open Issues

目前沒有 blocking methodology issue。需由 Sponsor/engineering reviewers 確認：

1. 是否要把第三方 Research candidate 升為 approved installable implementation；若要，source/license review、vendor/pin 與各 environment verification 是否完整。此項不阻塞 manual defaults。
2. P3/P2/P1/P0 的 minimum artifact pack 是否符合實際 team workflow。
3. P0 lightweight/JIT planning boundary，以及 P1/P0 OpenSpec Change scope rule 是否足夠直覺。
4. 各 Team 的 local activity／system-of-record mapping 與 Team-owned templates 是否能滿足 Department minimum contract，而不增加 duplicate artifacts。
5. 既有十個以上 pilot case inventory 的 evidence source、owner 與可公開於 Training 的 3–5 canonical cases。
6. Sponsor/Engineering 確認 04 v1.12、05 v1.12 與 Training v1.16 的 Six Questions entry、Stage-internal capability selection、OpenSpec task breakdown、problem clarity、P1 Feature Golden Path、active default adoption path、human judgment × AI execution notes、三個 target outcomes，以及 Design／Implement 各 1.5 週的 8 週 → 6 週 illustration 與 usability 後轉 Baseline。

---

## 15. Exact Next Action

下一個 working session 應依序完成以下 checklist；已完成的項目不要重做，只有受本次工作影響的 artifacts 才需要更新。

### Read Current Sources

- [ ] Read this section and `reference/Enforcement_E1_PR_Decision_Record.md`，including its copyable workflow／example PR。
- [ ] Consult `02_Framework.md` v1.12 changelog only if the enforcement、responsibility 或 Durable ledger boundary is unclear；do not reread unrelated framework artifacts。

### Start E1 Adoption

- [ ] Select one pilot Team／repository and one Tech Lead owner；do not roll out Department-wide。
- [ ] Confirm existing PR approval protection；copy `reference/enforcement/e1/human-decision-record.yml` and run `example-pr.md` on 2–3 PRs。
- [ ] Map an existing P0 label if available；otherwise keep approval-only mode，不為 automation 新增 P0 metadata。
- [ ] Enable one required check for the pilot and run it for 30 days。
- [ ] Record Team-level friction／false positives in Actions logs、PR history and one existing rollout issue；do not create a dashboard or score individuals。
- [ ] At day 30 decide keep／adjust／stop；do not enable Team-profile or dual-SSOT detection before that decision。

### Preserve Guardrails

- [ ] Use existing PR／CI／tracker records；do not add a system、form、meeting or dashboard。
- [ ] Do not modify `03_Golden_Engineering_Playbook.md`、`guides/04_Framework_Overview.md` or `guides/05_Decision_Tree.md` for E1 unless the pilot exposes an actual contradiction。

---

## 16. Handoff Confirmation Checklist

新 session 在開始前，應確認自己理解：

- [ ] 這是 AI-Native Software Engineering Framework，不是 tool manual。
- [ ] Charter 定義 direction，Handoff 定義 working rules，Framework 定義 method/governance，Golden Playbook 定義 engineering usage。
- [ ] Golden Flow 是唯一 Engineer workflow；新工作完整回答 Six Golden Questions，執行中更新 Current Stage／Next Move，context 改變時完整重判。
- [ ] `Understand → Challenge → Execute → Evidence` 是每個 Golden Stage 的 AI 基本功，不是第二套 workflow。
- [ ] Understand／Define／Design／Build／Verify／Release／Operate 只作 responsibility coverage，不是 formal lifecycle model。
- [ ] AI Execution Mode 只控制 AI authorization，不是 workflow。
- [ ] Governance 使用 System Criticality、L0–L3 Change Risk Tier 與 E0–E3 Execution Mode。
- [ ] Quality 使用 Understanding、Change、Evidence 三個 gates。
- [ ] AI output 不等於 completion；evidence 與 human accountability 才是 completion basis。
- [ ] Golden Flow 是 Research → Design → Plan → Implement → Validate；P3→P0 會遞迴套用但深度不同。
- [ ] Research 以不需安裝的 manual capability contract 作 active default；candidate skill 不阻塞工作，替換仍需先證明等價。
- [ ] Golden Stages 是 portable engineering decision states，不是 Department 統一 SDLC phases；Team 擁有 local workflow mapping。
- [ ] Hierarchy 是 P3 Product/Program → P2 Epic → P1 Feature → P0 PBI/User Story → Execution Layer；Task 不是 P0。
- [ ] `to-tickets` 只在 P1 包含多個獨立 outcome 時負責 P1 → 多個 P0；單一 bounded P1 直接作為 P0。Implementation breakdown 已採用 OpenSpec 時只用 `tasks.md`；未採用時才以 inline plan／triggered `writing-plans` 承接。
- [ ] System Design 位於 Design stage；P3/P2 required、P1 triggered、P0 normally skip。
- [ ] System Design Review 是 Change Gate implementation，不是第四個 universal gate。
- [ ] 要做什麼尚未清楚時，依第一個未知選 research、`grill-me` 或 `/opsx:explore`；不要全部固定串接。
- [ ] OpenSpec、Superpowers、`to-tickets`、`writing-plans` 都在 Current Stage 內選擇，不是 initial routing 或第二套 workflow。
- [ ] Clear、bounded P0/P1 可使用 existing SSOT + Superpowers／Team equivalent；需要 durable agreement/change traceability 時才由 OpenSpec 擁有 proposal/specs/design/tasks。
- [ ] OpenSpec 管 Spec-Driven Development；Superpowers 管 TDD-centered engineering disciplines。OpenSpec Change 只有一份 `tasks.md`，粗 task 原檔展開；改變做法走 `/opsx:update`，不得使用 `writing-plans` 或另建 ledger。
- [ ] 是否採用 OpenSpec，只作 Stage-internal artifact／execution selection；Engineer 入口仍是 Six Golden Questions，接著依 Golden Flow 定位 Current Stage。
- [ ] Enforcement 使用既有 PR／CI／tracker／GitOps chokepoints；不建立新 system、form、meeting 或 dashboard。
- [ ] 目前只啟用 E1 Human Decision Record on PR：P0 approval 本身是 record；non-P0 使用 gate label；Conditional Pass 必須 link issue。
- [ ] Team-profile gate preservation 是 Sampling、dual-SSOT detection 是 Detective；兩者已定義但未啟用。
- [ ] E1 先在一個 Team 跑 30 天，只看 Team-level friction／false positives，不對個人計分。
- [ ] Artifact contract 定義 information/evidence，不是 mandatory file；優先 reuse existing system of record，reference rather than copy。
- [ ] Department 定 minimum contract/quality bar；Team 定 templates、tracker、repository、technology/product/domain practices。
- [ ] E3 沿用既有 authorized owner、Change Management 與 production control；AI 不得成為 production approver。
- [ ] 已有十個以上 pilots 是 evidence base；下一步是 consolidation/canonical cases，不是重新要求 pilot。
- [ ] 03 v1.12 已是 Baseline；04 v1.12 與 05 v1.12 Candidate 維持 Six Questions → Current Stage → Stage-internal capability、conditional P1 slicing 與 OpenSpec task-breakdown summary；single-ledger/JIT breakdown 細節只由 03 管理。
- [ ] 06 v1.16 Candidate 已是實際 9 頁 PowerPoint；P3 是 responsibility ownership，P4 是 Six Questions → Current Stage → Stage-internal skills，P6 區分 delivery outcomes／implementation tasks 並維持 OpenSpec `tasks.md` single ledger，P7 將工具放回對應 Stage；P8 的 8 週 → 6 週仍是需由 pilots 校準的 illustration。已完成全頁 render、changed-slide inspection、overflow 與 template fidelity QA。
- [ ] README 已提供角色路徑；Engineer 必要閱讀 03 的對應章節，第一次接觸可選讀 04，routing ambiguity 才查 05。
- [ ] 05 開頭同時擔任 compact quick reference；不另外維護 `07` content SSOT。
- [ ] 下一步先完成 E1 30-day adoption；其後才依 evidence 決定其他 enforcement、pilot consolidation、Team adapter、optional candidate implementation review 與 Sponsor/Engineering confirmation。

---

## 17. Final Instruction to the Next AI

保留已確認的 project intent 與核心模型，像一個同時理解 enterprise transformation 與 production software engineering 的 principal consultant 工作。

**追求清楚、可執行、可驗證；優先減少不必要流程，不以文件厚度代替 framework quality。**
