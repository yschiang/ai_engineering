# AI Handoff — AI-Native Software Engineering Framework

> Version: v1.17  
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

這是 Engineer 唯一需要使用的 workflow。Engineer 用 Six Golden Questions 定位：

1. Current Work Location。
2. Work Level。
3. Archetype。
4. Current Golden Stage。
5. Control Profile。
6. Next Move：required capability、Golden default skill、artifact/evidence、gate owner。

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

Gates 是共同判斷語言，不強制新增三場會議或三份表格。

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

Plan stage 的兩層 decomposition 不得混用：

```text
P1 Feature / Approved Design
→ to-tickets
→ P0 PBI / Story vertical slices + Blocked by
→ writing-plans（單一 P0、JIT、risk/complexity triggered）
→ Execution Layer：Tasks / Plan Steps / Commits
→ TDD / Implement / Verify
```

不得先替整個 Epic 建立一份巨大 implementation plan。沒有 blocker 的 P0 形成 execution frontier；wide refactor 採 `expand → migrate batches → contract`。

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

`00–07` 共八個 artifacts。`00–03` 是 core operating assets；`04–07` 是由 core 衍生的 supplements。

| ID | Artifact | Format | Status / Purpose |
|---|---|---|---|
| 00 | `00_Project_Charter.md` | Markdown | v1.5 Baseline；單一 Engineer mental model 與 adoption positioning |
| 01 | `01_AI_Handoff.md` | Markdown | v1.17；future sessions 的工作控制文件 |
| 02 | `02_Framework.md` | Markdown，25–30 頁等級 | v1.6 Baseline；Golden model、responsibility coverage、integration 與治理 SSOT |
| 03 | `03_Golden_Engineering_Playbook.md` | Markdown | v1.4 Baseline；Golden Flow + Six Questions + Golden default skills |
| 04 | `diagrams/04_Framework_Overview.md` | Diagram / Markdown | v1.4 Candidate；單一 Engineer mental model overview，待 Sponsor review |
| 05 | `diagrams/05_Decision_Tree.md` | Diagram / Markdown | v1.5 Candidate；Six Questions 導向 capability、Golden default、placement 與 gate |
| 06 | `presentation/06_Training_Presentation.pptx` | PowerPoint，9 頁 | v1.8 Baseline Candidate；以單一 P1 Feature storyline 教 Golden Flow、Plan 與 Golden defaults，保留 8 週 → 6 週 target outcome |
| 07 | `07_Quick_Reference_Guide.*` | One Pager | Pending supplement；日常快速使用 |

Case Library 是既有十個以上 pilots 的持續演進 evidence collection；Team-specific templates 由 Team 管理。其他 bonus items 必須有真實 adoption need，避免文件/checklist 無限制增加。

---

## 6. Current Status

### Completed

- Project Charter 已重建為正式 artifact。
- AI Handoff 已重建為正式 artifact。
- `00_Project_Charter.md` v1.5 已將 Golden Flow + Six Golden Questions 定義為唯一 Engineer mental model。
- `02_Framework.md` v1.6 Baseline 已將七段內容降為 non-prescriptive responsibility coverage；`Understand → Challenge → Execute → Evidence` 改為每個 Golden Stage 的 AI 基本功。
- `03_Golden_Engineering_Playbook.md` v1.4 Baseline 已保留 Six Questions 完整定位能力，並加入 `required discipline + Golden default + approved equivalent` skill adoption policy。
- `diagrams/04_Framework_Overview.md` v1.4 Candidate 與 `diagrams/05_Decision_Tree.md` v1.5 Candidate 只呈現 Golden mental model、Six Questions 與 Golden default routing。
- `presentation/06_Training_Presentation.pptx` v1.8 Baseline Candidate 共 9 頁；移除重複的 stage matrix／skill policy／risk detail pages，改以單一 P1 Feature Golden Path 說明 Engineer 下一步、Golden default skill 與完成 evidence。8 週 → 6 週 target comparison 保留。

### Framework 已涵蓋

- Executive Summary、Purpose、Design Principles。
- Golden Flow + Six Golden Questions；每個 Stage 的 AI 基本功；E0–E3 AI Execution Mode。
- `System Criticality × L0–L3 Change Risk Tier × AI Execution Mode` Control Profile。
- Understand、Define、Design、Build、Verify、Release、Operate responsibility coverage；不是 formal lifecycle model。
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
3. Sponsor/Engineering 確認 `04` v1.4、`05` v1.5 與 `06` v1.8 的 single-mental-model narrative、Six Questions routing、P1 Feature Golden Path、Golden skill defaults、8 週 → 6 週 target assumptions 與 usability。
4. 核准後產生 `07_Quick_Reference_Guide` one pager；只呈現 Golden Flow + Six Questions + triggered controls，不引入七段 formal lifecycle。

---

## 7. Repository Blueprint

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
│   ├── source-material/
│   ├── examples/
│   └── review-feedback/
├── output/
│   ├── draft/
│   └── release/
├── reference/
│   ├── standards/
│   └── case-studies/
└── archive/
```

### I/O Rules

- `input/`：本輪直接使用的原始材料，不修改 source truth。
- `output/draft/`：可 review 的 working artifacts。
- `output/release/`：已通過 Definition of Done 的正式版本。
- `reference/`：影響判斷但不是本輪直接輸入的標準與案例。
- `archive/`：被取代但需保留追溯的版本。
- `assets/`：diagram、presentation 與 document 共用素材。

---

## 8. Source of Truth Hierarchy

| Priority | Artifact | Responsibility |
|---:|---|---|
| 1 | `00_Project_Charter.md` | Why、scope、non-goals、success criteria |
| 2 | `01_AI_Handoff.md` | Working rules、current status、next actions |
| 3 | `02_Framework.md` | Golden model、responsibility coverage、Tier、roles、gates、practices |
| 4 | `03_Golden_Engineering_Playbook.md` | Delivery Level、Archetype、skill → artifact → gate execution mapping |
| 5 | `04–07` | 由 Framework + Playbook 衍生的 communication/use supplements |
| 6 | Working notes / chat | 暫時 context，不得凌駕正式 artifacts |

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
- Quick Reference 必須一頁內可掃描使用。

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
11. 建立 `system-design` logical capability bundle、System Design Pack 與 System Design Review。
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

22. 以 Golden Stage 為 rows、P3–P0 為 columns，每格直接呈現 `Golden default skill/action → minimum output`。
23. 明確區分 P3/P2 delivery decomposition、P1 `to-tickets` 與 P0 JIT `writing-plans`。
24. Matrix output 作為下一 stage handoff，可存在既有 ticket/OpenSpec/ADR/PR，不新增 mandatory document。

`06_Training_Presentation.pptx` v1.0 Candidate 將 04/05 轉為 Department training storyline：

25. 10 頁依序回答 Why、Operating Model、Work Level、Golden Matrix、planning split、capability responsibility、controls/gates、common routes、roles 與 adoption mission。
26. Golden Matrix 是 training 中央操作面：先選 P3–P0 column，再找 Current Stage row，cell 直接給 `skill/action → output`。
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
63. Golden Matrix 每格明確使用 Golden default skill/action → minimum output；Decision Tree 以 Six Questions 導向 next move，不再要求 Engineer 同時記住兩套心智模型。
64. Training deck v1.7 共 12 頁；slide 3 將 AI Work Loop 改為 AI 基本功，slide 4 明示 single workflow + Six Questions，slides 6/8 強化 Golden defaults，slide 12 直接列出六個啟動問題。完成全頁 CJK render、逐頁 visual inspection、overflow、template fidelity 與 empty-placeholder QA。

`01` v1.17 與 `06` v1.8 完成 Feature-first presentation condensation：

65. Training deck 以 P1 Feature 作為唯一 teaching example；Work Level 只決定 depth，Task 仍位於 P0 下方 Execution Layer。
66. 原 slides 7–9 的 stage matrix、skill policy 與 risk detail，以及原 slide 10 的 walkthrough，合併成單一 Engineer operational takeaway：先把問題弄對、再把交付切小、最後用證據完成。
67. 合併頁明示 Golden Flow 決定 next step、Golden Default skill 決定 how、risk 只改變 rigor 不改變 route；避免工程師看完仍不知道下一步。
68. Plan 頁直接呈現 `Approved P1 → to-tickets → P0 vertical slices / Blocked by → triggered writing-plans → implementation tasks`。
69. Outcome 頁明示總時間 `8 → 6 weeks (-25%)`；final deck 共 9 頁，完成全頁 CJK render、逐頁 visual inspection、overflow、template fidelity、page marker 與 empty-placeholder QA。

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

- Engineer 能在 60 秒內回答 Six Golden Questions，依 Current Work Location、Work Level、Archetype、Current Stage 與 Control Profile 找到 next move。
- P3 Greenfield、P3 Modernization/Migration、P2 Epic、P1 Feature、P0 PBI/User Story（含 Story/Enabler/Bug/Spike）都有 flow。
- 每個 stage 明確對應 skill、artifact 與 human gate。
- 新手可直接採用 Golden default skill path；Team equivalent 有明確 mapping contract。
- 每個 stage 明確說明 typical existing activity、artifact location、decision owner 與是否需 additional process；local mapping 由 Team 擁有。
- OpenSpec 與 Superpowers responsibility split 清楚，且不建立雙份 design/plan。
- System Design 在 P3/P2 與 triggered P1 可被直接選到；P0 不被強制套用。
- System Design Review 是 Change Gate implementation，沒有新增 universal gate。

### 04 Framework Overview

- 一頁看懂 Golden Flow、Six Golden Questions、AI 基本功、Control Profile、gates 與 outcome。
- 明確呈現 P3 → P2 → P1 → P0 → Execution Layer，以及 `to-tickets` / per-P0 JIT `writing-plans` 分工。
- 不把 responsibility coverage 或 AI 基本功畫成第二套 Engineer workflow。
- 不依賴長篇文字才能理解基本關係。

### 05 Decision Tree

- 能從 change context 判定 Tier。
- 能在 60 秒內由 existing work location、largest unknown/risk、Work Level、P0 type、Archetype、System Design trigger 與 Control Profile 導向 next skill、artifact placement 與 gate。
- 保留 P1 → P0 `to-tickets`、per-P0 JIT `writing-plans`、Task as Execution Layer 與 OpenSpec P1/P0 scope rule。
- 能導向必要 understanding、design、verification 與 release controls。
- 不將每條路徑導向相同流程。

### 06 Training Presentation

- 8–12 頁 PowerPoint；以最短可教會 Engineer 的 storyline 為準。
- Storyline 清楚，適合 Department Meeting 或 training。
- 包含 Why now、existing workflow enhancement、model、how to work、roles、Team adapter/call to action。

### 07 Quick Reference Guide

- One Pager。
- 能在 task 啟動、review 與 release 前快速使用。
- 不只是 Framework 目錄縮寫。

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
- 把 Golden default skills 降成可忽略的建議清單；未完成 approved-equivalent mapping 前，應直接採用 defaults。
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

1. Department skill aliases 與可用 environment mappings 是否完整。
2. P3/P2/P1/P0 的 minimum artifact pack 是否符合實際 team workflow。
3. P0 lightweight/JIT planning boundary，以及 P1/P0 OpenSpec Change scope rule 是否足夠直覺。
4. 各 Team 的 local activity／system-of-record mapping 與 Team-owned templates 是否能滿足 Department minimum contract，而不增加 duplicate artifacts。
5. 既有十個以上 pilot case inventory 的 evidence source、owner 與可公開於 Training 的 3–5 canonical cases。
6. Sponsor/Engineering 確認 04 v1.4、05 v1.5 與 06 v1.8 的 single-model clarity、P1 Feature Golden Path、Golden default adoption path、density、routing correctness、8 週 → 6 週 illustration 與 usability 後轉 Baseline。

---

## 15. Exact Next Action

下一個 working session 應執行：

> **Read `00_Project_Charter.md` v1.5, `01_AI_Handoff.md` v1.17, `02_Framework.md` v1.6 Baseline, `03_Golden_Engineering_Playbook.md` v1.4 Baseline, `diagrams/04_Framework_Overview.md` v1.4 Candidate, `diagrams/05_Decision_Tree.md` v1.5 Candidate, and `presentation/06_Training_Presentation.pptx` v1.8 Baseline Candidate. Validate that Golden Flow + Six Golden Questions is the single Engineer mental model and that new users can follow the P1 Feature Golden Path and Golden default skill path without prior skill knowledge. Consolidate the existing 10+ pilots and select 3–5 canonical cases; define Team-owned local workflow adapters without centralizing templates. After Sponsor/Engineering confirms 04–06, create `07_Quick_Reference_Guide` with Six Questions as its top router. Do not create a parallel SDLC, another formal lifecycle, or another generic checklist.**

---

## 16. Handoff Confirmation Checklist

新 session 在開始前，應確認自己理解：

- [ ] 這是 AI-Native Software Engineering Framework，不是 tool manual。
- [ ] Charter 定義 direction，Handoff 定義 working rules，Framework 定義 method/governance，Golden Playbook 定義 engineering usage。
- [ ] Golden Flow + Six Golden Questions 是唯一 Engineer mental model。
- [ ] `Understand → Challenge → Execute → Evidence` 是每個 Golden Stage 的 AI 基本功，不是第二套 workflow。
- [ ] Understand／Define／Design／Build／Verify／Release／Operate 只作 responsibility coverage，不是 formal lifecycle model。
- [ ] AI Execution Mode 只控制 AI authorization，不是 workflow。
- [ ] Governance 使用 System Criticality、L0–L3 Change Risk Tier 與 E0–E3 Execution Mode。
- [ ] Quality 使用 Understanding、Change、Evidence 三個 gates。
- [ ] AI output 不等於 completion；evidence 與 human accountability 才是 completion basis。
- [ ] Golden Flow 是 Research → Design → Plan → Implement → Validate；P3→P0 會遞迴套用但深度不同。
- [ ] Skill adoption 是 `required discipline + Golden default + approved equivalent`；新手直接採 default，替換需先證明等價。
- [ ] Golden Stages 是 portable engineering decision states，不是 Department 統一 SDLC phases；Team 擁有 local workflow mapping。
- [ ] Hierarchy 是 P3 Product/Program → P2 Epic → P1 Feature → P0 PBI/User Story → Execution Layer；Task 不是 P0。
- [ ] `to-tickets` 負責 P1 → P0；`writing-plans` 只在單一 P0 即將執行且風險/複雜度觸發時使用。
- [ ] System Design 位於 Design stage；P3/P2 required、P1 triggered、P0 normally skip。
- [ ] System Design Review 是 Change Gate implementation，不是第四個 universal gate。
- [ ] OpenSpec 管 durable change agreement，Change 可承載 P1/P0；Superpowers 管 execution discipline；Explore 保持 E0/no-artifact。
- [ ] Artifact contract 定義 information/evidence，不是 mandatory file；優先 reuse existing system of record，reference rather than copy。
- [ ] Department 定 minimum contract/quality bar；Team 定 templates、tracker、repository、technology/product/domain practices。
- [ ] E3 沿用既有 authorized owner、Change Management 與 production control；AI 不得成為 production approver。
- [ ] 已有十個以上 pilots 是 evidence base；下一步是 consolidation/canonical cases，不是重新要求 pilot。
- [ ] 03 v1.4 已是 Baseline；04 v1.4 與 05 v1.5 Candidate 已同步 single-model／Golden-default correction。
- [ ] 06 v1.8 Baseline Candidate 已是實際 9 頁 PowerPoint；以 Golden Flow + Six Questions 啟動、用單一 P1 Feature Golden Path 強化 Golden defaults，target outcome 保留 8 週 → 6 週 illustration，並完成 CJK render、逐頁 visual inspection、overflow 與 template fidelity QA。
- [ ] 下一步是 pilot consolidation、Team adapter 與 Sponsor/Engineering confirmation；其後建立 `07_Quick_Reference_Guide` one pager。

---

## 17. Final Instruction to the Next AI

保留已確認的 project intent 與核心模型，像一個同時理解 enterprise transformation 與 production software engineering 的 principal consultant 工作。

**追求清楚、可執行、可驗證；優先減少不必要流程，不以文件厚度代替 framework quality。**
