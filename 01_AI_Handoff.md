# AI Handoff — AI-Native Software Engineering Framework

> Version: v1.13  
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
- End-to-end lifecycle framework。
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

## 4. Confirmed Core Models

### 4.1 Engineering Lifecycle

```text
Understand → Define → Design → Build → Verify → Release → Operate
```

用途：描述一項 engineering change 從理解到 production learning 的完整 lifecycle。

### 4.2 AI Work Loop

```text
Understand → Challenge → Execute → Evidence
```

用途：描述任何 lifecycle stage 內，人與 AI 應採用的共同工作閉環。

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

### 4.8 Practical Capability Chain

```text
Understand → Explore → Define → Design → Challenge → Plan → Implement → Verify → Release
```

Golden Playbook 收斂為 `Research → Design → Plan → Implement → Validate`。OpenSpec `/opsx:explore` 是目前 Explore capability 的 E0 reference implementation；它不建立 change artifact/code，若繼續則由 proposal/specs/design/tasks 承接。

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

System Design 位於 Design stage 內，不是新的 lifecycle stage：

- P3 Product/Program：Required。
- P2 Epic：Required。
- P1 Feature：跨 boundary/contract/data、重大 NFR、novel architecture 或 L2–L3 時 triggered。
- P0 PBI / Story：Normally skip；觸及 architecture boundary 時升級處理。

System Design Review 是 Change Gate 的 risk-based implementation，不是第四個 Universal Quality Gate。P3/P2 architecture 使用 Product/Architecture SSOT；P1 可由 OpenSpec `design.md` 承載，避免重複文件。

---

## 5. Deliverable Architecture

`00–07` 共八個 artifacts。`00–03` 是 core operating assets；`04–07` 是由 core 衍生的 supplements。

| ID | Artifact | Format | Status / Purpose |
|---|---|---|---|
| 00 | `00_Project_Charter.md` | Markdown | Completed；專案目的、scope、principles、success criteria |
| 01 | `01_AI_Handoff.md` | Markdown | Completed；future sessions 的工作控制文件 |
| 02 | `02_Framework.md` | Markdown，25–30 頁等級 | v1.4 Baseline completed；完整方法與治理 SSOT |
| 03 | `03_Golden_Engineering_Playbook.md` | Markdown | v1.2 Baseline completed；Engineer-facing Golden Reference |
| 04 | `diagrams/04_Framework_Overview.md` | Diagram / Markdown | v1.2 Candidate；已完成 one-page density targeted patch，待 Sponsor review |
| 05 | `diagrams/05_Decision_Tree.md` | Diagram / Markdown | v1.3 Candidate；Golden Matrix 明確加入 Archetype／Control Profile overlay rule，待 Sponsor/Engineering review |
| 06 | `presentation/06_Training_Presentation.pptx` | PowerPoint，11 頁 | v1.4 Baseline Candidate；以 8 週 → 5.5 週示意 AI Engineering target outcome，待 Sponsor/Engineering confirmation |
| 07 | `07_Quick_Reference_Guide.*` | One Pager | Pending supplement；日常快速使用 |

Bonus items，例如 prompt matrix、case library、detailed templates，必須在核心 artifacts 完成後再決定。

---

## 6. Current Status

### Completed

- Project Charter 已重建為正式 artifact。
- AI Handoff 已重建為正式 artifact。
- `02_Framework.md` 已完成 semantic correction 與 v1.4 Baseline。
- `03_Golden_Engineering_Playbook.md` v1.2 Baseline 已完成 Work Level、`to-tickets` / `writing-plans` 與 tracker mapping correction。
- `diagrams/04_Framework_Overview.md` v1.2 Candidate 已壓縮 capability/gate/tracker detail，保留一頁核心決策。
- `diagrams/05_Decision_Tree.md` v1.3 Candidate 已補齊 top-level 60-second router、P3–P0 × Stage skill/output matrix、P1/P0 boundary、Release/Operate overlay、explicit OpenSpec next actions，並明確 Archetype／Control Profile 是調整 depth 的 overlay，不是第三個 Matrix 軸。
- `presentation/06_Training_Presentation.pptx` v1.4 Baseline Candidate 已將 target outcome comparison 修正為 calendar-time illustration：示例 Feature 從 8 週縮短至 5.5 週（約 3 個 two-week Sprints）；Research 時間相近但更有效，Design 增至 1 週、Validate 略增，Implementation stage 明顯縮短。圖表以 PNG 嵌入，並標示需由 pilot actual baseline 校準。

### Framework 已涵蓋

- Executive Summary、Purpose、Design Principles。
- Engineering Lifecycle、AI Work Loop 與 E0–E3 AI Execution Mode。
- `System Criticality × L0–L3 Change Risk Tier × AI Execution Mode` Control Profile。
- Understand、Define、Design、Build、Verify、Release、Operate 七階段。
- Role Expectations。
- Core Use Cases。
- Artifact Model 與 Repository/I/O Blueprint。
- P3–P0 Delivery Level、Work Archetype 與 Practical Capability Chain。
- System Design capability、trigger、System Design Pack、Change Gate review 與 architecture/OpenSpec SSOT boundary。
- P1 → P0 delivery slicing、P0 → Execution Layer JIT planning、dependency frontier 與 tracker reference mapping。
- Reusable Working Patterns。
- Three Quality Gates。
- Definition of Done。
- Metrics、Adoption Model、Anti-patterns、Decision Guide、Templates 與 Governance。

### Next Required Work

1. Sponsor/Engineering confirmation `presentation/06_Training_Presentation.pptx` v1.4 Baseline Candidate 的 storyline、Golden Matrix routing correctness、8 週 → 5–6 週 target assumptions、training pacing 與 call to action。
2. Sponsor/Engineering 同步確認 `diagrams/04_Framework_Overview.md` v1.2 與 `diagrams/05_Decision_Tree.md` v1.3 後轉 Baseline。
3. 依已確認的 04–06 產生 `07_Quick_Reference_Guide` one pager。

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
| 3 | `02_Framework.md` | Capability model、Tier、lifecycle、roles、gates、practices |
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
7. `Understand → Explore → Define → Design → Challenge → Plan → Implement → Verify → Release` Practical Capability Chain。
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

22. 以 Golden Stage 為 rows、P3–P0 為 columns，每格直接呈現 `lead skill/action → minimum output`。
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

- Engineer 能在 60 秒內依 Work Level、Archetype、Current Stage、Control Profile 找到 next move。
- P3 Greenfield、P3 Modernization/Migration、P2 Epic、P1 Feature、P0 PBI/User Story（含 Story/Enabler/Bug/Spike）都有 flow。
- 每個 stage 明確對應 skill、artifact 與 human gate。
- OpenSpec 與 Superpowers responsibility split 清楚，且不建立雙份 design/plan。
- System Design 在 P3/P2 與 triggered P1 可被直接選到；P0 不被強制套用。
- System Design Review 是 Change Gate implementation，沒有新增 universal gate。

### 04 Framework Overview

- 一頁看懂 Lifecycle、Work Loop、Execution Mode、Control Profile、gates 與 outcome。
- 明確呈現 P3 → P2 → P1 → P0 → Execution Layer，以及 `to-tickets` / per-P0 JIT `writing-plans` 分工。
- 不依賴長篇文字才能理解基本關係。

### 05 Decision Tree

- 能從 change context 判定 Tier。
- 能在 60 秒內由 Work Level、P0 type、Archetype、System Design trigger、Control Profile、Current Stage 導向 next skill、artifact 與 gate。
- 保留 P1 → P0 `to-tickets`、per-P0 JIT `writing-plans`、Task as Execution Layer 與 OpenSpec P1/P0 scope rule。
- 能導向必要 understanding、design、verification 與 release controls。
- 不將每條路徑導向相同流程。

### 06 Training Presentation

- 10–12 頁 PowerPoint。
- Storyline 清楚，適合 Department Meeting 或 training。
- 包含 Why now、model、how to work、roles、mission/call to action。

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
- 把所有 practices 設為 mandatory。
- 用更多文件解決 ownership 或 judgment 問題。
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
4. Sponsor/Engineering 確認 04 Overview 與 05 Decision Tree 的 density、terminology、routing correctness 與 usability 後轉 Baseline。
5. Training Presentation v1.4 Baseline Candidate 的 11 頁 pacing、Golden Matrix routing correctness、8 週 → 5–6 週 calendar allocation assumptions 與 team mission 是否適合 Department Meeting。

---

## 15. Exact Next Action

下一個 working session 應執行：

> **Read `00_Project_Charter.md` v1.3, `01_AI_Handoff.md` v1.13, `02_Framework.md` v1.4, `03_Golden_Engineering_Playbook.md` v1.2 Baseline, `diagrams/04_Framework_Overview.md` v1.2 Candidate, `diagrams/05_Decision_Tree.md` v1.3 Candidate, and `presentation/06_Training_Presentation.pptx` v1.4 Baseline Candidate. Confirm the Golden Matrix routing correctness, deck storyline, representative routes, 8 週 → 5–6 週 target assumptions, roles and team mission. After approval, create `07_Quick_Reference_Guide` as a true one-page start/review/release aid derived from 04–06; do not compress the Framework table of contents into a page.**

---

## 16. Handoff Confirmation Checklist

新 session 在開始前，應確認自己理解：

- [ ] 這是 AI-Native Software Engineering Framework，不是 tool manual。
- [ ] Charter 定義 direction，Handoff 定義 working rules，Framework 定義 method/governance，Golden Playbook 定義 engineering usage。
- [ ] Lifecycle、AI Work Loop 與 AI Execution Mode 是三個不同控制維度。
- [ ] Governance 使用 System Criticality、L0–L3 Change Risk Tier 與 E0–E3 Execution Mode。
- [ ] Quality 使用 Understanding、Change、Evidence 三個 gates。
- [ ] AI output 不等於 completion；evidence 與 human accountability 才是 completion basis。
- [ ] Golden Flow 是 Research → Design → Plan → Implement → Validate；P3→P0 會遞迴套用但深度不同。
- [ ] Hierarchy 是 P3 Product/Program → P2 Epic → P1 Feature → P0 PBI/User Story → Execution Layer；Task 不是 P0。
- [ ] `to-tickets` 負責 P1 → P0；`writing-plans` 只在單一 P0 即將執行且風險/複雜度觸發時使用。
- [ ] System Design 位於 Design stage；P3/P2 required、P1 triggered、P0 normally skip。
- [ ] System Design Review 是 Change Gate implementation，不是第四個 universal gate。
- [ ] OpenSpec 管 durable change agreement，Change 可承載 P1/P0；Superpowers 管 execution discipline；Explore 保持 E0/no-artifact。
- [ ] 03 v1.2 已是 Baseline；04 v1.2 與 05 v1.3 Candidate 已完成 targeted revision + corrected Golden Matrix。
- [ ] 06 v1.4 Baseline Candidate 已是實際 11 頁 PowerPoint；target outcome slide 使用 8.0 週 → 5.5 週 calendar-time illustration，bar chart 為嵌入式 PNG，並完成 CJK render、逐頁 visual inspection、overflow 與 template fidelity QA。
- [ ] 下一步是 confirm 06 v1.4 的 routing、cycle-time assumptions 與 pacing；核准後建立 `07_Quick_Reference_Guide` one pager。

---

## 17. Final Instruction to the Next AI

保留已確認的 project intent 與核心模型，像一個同時理解 enterprise transformation 與 production software engineering 的 principal consultant 工作。

**追求清楚、可執行、可驗證；優先減少不必要流程，不以文件厚度代替 framework quality。**
