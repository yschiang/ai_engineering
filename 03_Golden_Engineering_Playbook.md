# Department Golden Engineering Playbook

> Version: v1.5 Baseline
> Status: Baseline  
> Purpose: Engineer-facing execution guide for AI-Native Software Engineering  
> Governing Framework: `02_Framework.md` v1.7
> Audience: Engineer, Senior Engineer, Tech Lead, Architect, Engineering Manager

---

## Executive Statement

這份 Playbook 是部門級的 **Golden Reference**。它不是另一份治理文件或平行 SDLC，而是工程師在既有 ticket、design、PR、test、release 與 incident activities 中可以直接使用的入口。

每項工作只需要先回答六個問題：

1. **Current Work Location**：工作現在存在於哪個 Team activity／system of record？
2. **Work Level**：這是 Product/Program、Epic、Feature，還是 PBI/User Story？
3. **Archetype**：Greenfield、Legacy Modernization/Migration，還是 Standard Delivery？
4. **Current Golden Stage**：最大的未知或風險屬於 Research、Design、Plan、Implement、Validate 哪一類？
5. **Control Profile**：System Criticality、Change Risk Tier、AI Execution Mode 是什麼？
6. **Next Move**：現在應使用哪個 skill，在哪裡留下什麼 artifact，通過哪個 gate？

Golden Flow 是 Engineer 唯一需要使用的 workflow：

```text
Research → Design → Plan → Implement → Validate
```

Golden Stages 是可攜式 engineering decision states，不是所有 Team 必須採用的固定 SDLC phases。Team 可以把一個 activity mapping 到多個 Golden Stages，也可以讓一個 Golden Stage 跨活動或 Sprint。

在每個 Golden Stage，都使用同一組 **AI 基本功**：先 `Understand`、再 `Challenge`，接著 `Execute` 並留下 `Evidence`。它是每個 Stage 的工作紀律，不是第二套 lifecycle。

**核心規則：在既有工作位置處理當前最大的未知或風險，補齊 minimum information 與 gate decision；不要一次啟動所有 skills。**

---

## 1. How to Use This Playbook in 60 Seconds

### Step 0 — 找到 Existing Work Location

先確認工作目前在哪裡管理：backlog/ticket、refinement、design/RFC、branch/PR、pipeline/test、release/change record、dashboard/incident review，或 Team 的其他 system of record。

- 優先把 artifact/evidence 寫回既有 system of record。
- 一個 existing activity 可以承載多個 Golden Stages；不要硬把 Team workflow 改成五個 phases。
- 若沒有現成位置，才依 risk、handoff 與 longevity 建立 durable artifact。

### Step 1 — 選 Work Level

| Level | 你正在做的事情 | Start Here |
|---|---|---|
| **P3 Product / Program** | Greenfield product、legacy modernization、migration、長期 platform initiative | 先建立 Product/Program Brief，再拆 Epics |
| **P2 Epic** | 跨 feature/component 的完整 capability | 先做 Epic Research/Design，再拆 Features |
| **P1 Feature** | 可獨立驗收、部署或 feature-flag 控制的 outcome | 走完整 Golden Flow，再切成 P0 vertical slices |
| **P0 PBI / User Story** | Sprint-ready、narrow but complete、可獨立驗證的 vertical slice | 使用 P0 Flow；即將執行時才拆 tasks |

P0 類型可為 **User Story、Engineering Story / Enabler、Bug、Spike**。Spike 必須 time-boxed，以 evidence/decision outcome 獨立驗證；不強求 production demo。

**Execution Layer**：Task / Plan Step / Commit 位於 P0 下方，不是 Work Level。`Change` 也不是固定層級；OpenSpec Change 依 scope 承載 P1 或 P0 的 durable agreement。

### Step 2 — 選 Archetype

| Archetype | 主要未知 | Research 重點 |
|---|---|---|
| **Greenfield Product** | 問題、domain、boundary、MVP、architecture runway | 使用者/流程、domain model、system context、NFR、option exploration |
| **Legacy Modernization / Migration** | 真實 behavior、dependency、data、hidden rule、cutover risk | As-is research、characterization、compatibility、migration/recovery |
| **Standard Delivery** | Change impact、existing pattern、acceptance、failure mode | Targeted codebase research、bounded design、risk-specific validation |

### Step 3 — 找到 Current Stage

| Stage | 如果你現在還不能回答… | Golden Default Skills |
|---|---|---|
| Research | 系統/問題現在如何運作？有哪些 options？真正 scope 是什麼？ | `understand-anything` / `codebase-research` / `grill-me` / `/opsx:explore` |
| Design | 是否需要 System Design？要改成什麼、為什麼選這個方案？ | `system-design` when triggered / `superpowers:brainstorming` / `grill-with-docs` |
| Plan | 是把 P1 切成哪些 P0，還是把單一 P0 切成哪些 execution tasks？ | `to-tickets` / triggered `superpowers:writing-plans` |
| Implement | 如何按計畫小步實作並持續驗證？ | `test-driven-development` + execution skill |
| Validate | 有什麼 fresh evidence 證明完成？ | code review + `verification-before-completion` |

### Step 4 — 套 Control Profile

```text
Control Profile = System Criticality × Change Risk Tier × AI Execution Mode
```

Playbook 決定「怎麼做」；Control Profile 決定「需要做到多嚴謹」。

### Step 5 — 只執行下一個 Action

| Current State | Next Action |
|---|---|
| 有 problem，但需求、scope 或 option 還模糊 | `/opsx:explore` |
| Existing system 不熟，尚未找到真實 behavior/change boundary | `codebase-research`；範圍更廣時加 `understand-anything` |
| 規則主要在人的經驗裡 | `grill-me` |
| P3/P2，或 P1 涉及跨 boundary/contract/data、重大 NFR、novel architecture、L2+ | `system-design` capability bundle；完成 System Design Review |
| Direction 已清楚，需要 durable change agreement | `/opsx:propose`；複雜 change 用 `/opsx:new` + `/opsx:continue` |
| P1 Feature / Approved Design 尚未切成 sprint-ready slices | `to-tickets`：產生 P0 tracer bullets、`Blocked by` 與 execution frontier |
| 單一 P0 即將執行，且為 multi-step / high-risk / complex | `superpowers:writing-plans`：產生 exact-files implementation plan |
| P0 與必要 plan 已 ready | `/opsx:apply` + TDD/execution skills |
| Implementation ready，需要宣稱完成 | code review + `verification-before-completion`；再 sync/archive |

**不要先問「全部要跑哪些 skills」；先問「現在最大的未知或下一個 gate 是什麼」。**

本表列的是 Department **Golden defaults**。尚未建立成熟方法的 Engineer／Team 直接使用 defaults；成熟 Team 可以採用 registry 中的 equivalent skill，但必須接受相同 required inputs、產出相同 minimum artifact、遵守相同 stop condition、通過相同 gate，並保留相同 evidence quality。

---

## 2. Golden Delivery Flow

### 2.1 Golden Flow — The Only Engineer Workflow

| Golden Stage | Covered Capabilities | Engineer 的核心問題 |
|---|---|---|
| Research | Understand + Explore + Define | 現況、問題、boundary、options、unknowns 與 scope 是什麼？ |
| Design | System Design when triggered + Feature/Detailed Design + Challenge | Boundary、target behavior、architecture、trade-offs、failure behavior 是否站得住腳？ |
| Plan | Delivery decomposition + JIT implementation planning | 如何先切 P0 vertical slices，再按需將單一 P0 切成 execution tasks？ |
| Implement | TDD + bounded execution | 如何依 plan 以 TDD/controlled change 完成？ |
| Validate | Verify + release handoff | Requirement、risk、quality 是否有 fresh evidence？ |
| Release / Operate | Existing SDLC overlay | 如何安全 release、observe、rollback/recover、learn？ |

Release 與 Operate 不從 Golden Flow 消失；它們由既有 release/change/SRE process 承接，並使用 Validate stage 產生的 evidence。

這張表只展開 Golden Stage 內部涵蓋的 capabilities，不定義第二套 lifecycle。Team 的 Intake、Refinement、Sprint、PR、Release 或 Incident flow 可以合併、改名、重排；只要保留 Golden Stage 的工程問題、minimum contract、decision owner 與 risk-based evidence。

Shared／external／production action 必須經既有 Release／Change Management 與 authorized owner：

```text
Verified Change → Release Readiness → Existing Change Approval
→ Explicit E3 Authorization → Execute → Observe → Validate
→ Recover / Rollback if required
```

AI 可以準備 plan、validation、rollback 與 evidence，但不能成為 production approver；irreversible migration、destructive operation 與 production mutation 一律需要 explicit authorization。

### 2.2 OpenSpec and Golden Skills — Responsibility Split

OpenSpec 與 Golden Skills 互補，不應產生兩套重複文件：

| Capability | Primary Responsibility |
|---|---|
| OpenSpec | 維護 durable change agreement：proposal、specs、design、tasks、implementation alignment、archive |
| Understand / Research skills | 建立可信 system/domain/code understanding，提供 proposal/design 的 evidence basis |
| Grill skills | 外顯 tacit knowledge、挑戰 artifacts、關閉 ambiguity/contradiction |
| Delivery decomposition skill | 將 approved P1 Feature 切成 P0 tracer-bullet tickets、dependencies 與 execution frontier |
| Superpowers | 提供 design、P0 implementation planning、TDD、execution、review、verification 的工程紀律 |

OpenSpec Change 是 durable artifact container，不是 Work Level；每個 change 必須標示承載 P1 或 P0 scope。P1-scoped Change 的 `tasks.md` 記錄或引用 `to-tickets` 產生的 P0 ticket set/dependencies；P0-scoped Change 的 `tasks.md` 才承載 Execution Layer steps。若單一 P0 的 `tasks.md` 已達 executable plan 標準，不再建立第二份重複 plan；只需用 `writing-plans` 的品質標準補強或引用詳細 plan。

### 2.3 Combined Golden Workflow

OpenSpec 是 actions，不是另一套 rigid phases。Engineer 依當前狀態選下一個 action。

**Default Feature Path**：

```text
/opsx:explore (optional, when fuzzy)
→ /opsx:propose
→ grill-with-docs → approve P1 proposal/spec/design
→ to-tickets: P0 vertical slices + Blocked by
→ record/reference P0 set in OpenSpec tasks.md
→ for each frontier P0: writing-plans when triggered
→ /opsx:apply using TDD + execution skills
→ code review + verification
→ /opsx:sync → /opsx:archive
```

**Complex / Brownfield Path**：

```text
understand-anything + codebase-research + grill-me
→ /opsx:explore
→ /opsx:new + /opsx:continue, or /opsx:propose
→ grill-with-docs → approve P1 proposal/spec/design
→ to-tickets: P0 tracer bullets + dependency frontier
→ record/reference P0 set in P1 tasks.md
→ JIT executable tasks using writing-plans quality
→ /opsx:apply + TDD
→ review + /opsx:verify
→ /opsx:sync → /opsx:archive
```

核心責任邊界：

1. **OpenSpec owns durable agreement**：proposal 說 why、specs 說 what、design 說 how、tasks 依 declared scope 記錄 delivery references 或 execution steps，archive 回到 source of truth。
2. **Delivery decomposition owns P1 → P0**：`to-tickets` 產生 narrow but complete、demoable、independently verifiable 的 tracer bullets，並標示 blockers。
3. **Superpowers owns P0 execution discipline**：design refinement、JIT implementation planning、TDD、bounded execution、review、fresh verification。
4. **Explore is E0 and ephemeral**：只讀取、分析、比較與釐清，不建立 change folder、artifact 或 code；決定要做時，必須由 `propose` 或 `new/continue` 將結論固化。

System Design 的 SSOT 依 scope 決定：P3/P2 的 product/target architecture 放在 Product/Architecture SSOT，OpenSpec change 只引用或記錄 bounded architecture delta；P1 的 Feature/System Design 可以直接由 OpenSpec `design.md` 承載。

### 2.4 Universal Stage Contract

每個 stage 都應有：

```text
Input → Required Capability → Golden Default Skill → Activity → Artifact → Human Gate
```

Golden default 提供新手可直接採用的安全路徑；Team equivalent 必須在 Skill Registry 完成 capability、input/output、stop condition、gate 與 evidence mapping。

Artifact 可以存在既有 ticket、PR、design document、test report 或 dashboard，不強制每一步新增一份 Markdown。

### 2.5 Recursion Rule

大型工作不能直接從 Product Design 跳到大量 code：

```text
P3 Product / Program
  └─ P2 Epic
       └─ P1 Feature
            └─ P0 PBI / User Story
                 └─ Execution Layer: Task / Plan Step / Commit
```

- P3 決定 direction、boundary、architecture runway 與 decomposition。
- P2 決定 capability design、cross-feature contracts 與 release slices。
- P1 決定 bounded outcome、feature behavior，並用 `to-tickets` 切成 P0 vertical slices。
- P0 是可進 Sprint、可獨立驗證的 delivery slice；即將執行時才按需產生 implementation plan。
- Execution Layer 執行最小 test/change/review loop，不升格為 Delivery Level。

每個 level 都有自己的 Research → Design → Plan → Implement → Validate，但深度不同。

---

## 3. Department Skill Catalog

### 3.1 Skill Family A — Understand and Research

| Skill | Use When | Primary Output | Stop Condition |
|---|---|---|---|
| **`understand-anything`** | Domain/system unfamiliar、資料跨多來源、需要建立全貌 | Knowledge map、glossary、system/domain model、unknowns | 能描述 boundary、flow、critical concepts 與 unknowns |
| **`codebase-research`** | 既有 repository、需要以 code/test/history 證明 behavior | Code map、entry points、call/data flow、patterns、evidence links | Change boundary 與 existing pattern 已定位 |
| **`grill-me`** | 需求/規則主要在 Owner 或 operator 腦中 | Structured Q&A、decisions、assumptions、examples、open questions | Material tacit knowledge 已外顯並確認 |
| **`grill-with-docs`** | 已有 PRD/design/runbook，需要嚴格挑戰 | Evidence-based findings、missing cases、decision questions | Blocker ambiguity/contradiction 已關閉 |
| **`superpowers:systematic-debugging`** | Bug、incident、test failure、unexpected runtime behavior | Facts、hypotheses、falsification result、root cause | Root cause 有 reproduction/evidence，不是猜測 |

### 3.2 Skill Family B — OpenSpec Change Agreement

| OpenSpec Action | Use When | Primary Result | Stop / Handoff |
|---|---|---|---|
| **`/opsx:explore`** | 有 problem 但還沒有 plan；需求模糊、option 未決、scope 不確定 | 對話中的 evidence、options、trade-offs、scope clarity；**不產生 durable artifact/code** | 不做則停止；要做則交給 `propose` 或 `new` |
| **`/opsx:propose`** | Change intent 已足夠清楚，需要一次建立 change agreement | Proposal、specs、design、tasks | Human review agreement；再進 `apply` |
| **`/opsx:new` + `/opsx:continue`** | Expanded profile；複雜 change 需要逐步建立 artifacts | 逐步完成 proposal → specs → design → tasks | Required artifacts ready；再進 `apply` |
| **`/opsx:ff`** | Scope 已清楚，想快速建立全部 planning artifacts | Ready-for-apply change package | Review completeness；再進 `apply` |
| **`/opsx:apply`** | Change package 已可執行 | Implementation + updated task state | Tasks implemented；進 review/verify |
| **`/opsx:verify`** | Expanded profile；需要檢查 implementation 與 artifacts 一致 | Completeness、correctness、coherence findings | Findings closed；進 sync/archive |
| **`/opsx:sync` + `/opsx:archive`** | Change 已驗證，需要更新 source of truth 並封存 | Delta specs merged、completed change archived | Durable truth 可供下一次 change 使用 |

**OpenSpec artifact chain**：

```text
proposal (why) → specs (what) → design (how) → tasks (steps) → implementation
```

這條 artifact chain 不代表 hierarchy。OpenSpec Change 必須宣告 scope：coherent P1 Feature，或需要 durable agreement/handoff 的 P0 PBI；不得把 `Change` 當成 P0 同義詞。

### 3.3 Choosing the Research / Explore Tool

| Need | Start With | Why |
|---|---|---|
| 建立跨文件、domain、system 的整體理解 | `understand-anything` | 產生 structured knowledge model 與 unknowns |
| 找出既有 code 的真實 behavior、entry point、dependency | `codebase-research` | 以 repository evidence 定位 change boundary |
| 把 Owner/operator 腦中的規則問出來 | `grill-me` | 外顯 tacit knowledge、examples 與 decisions |
| 有問題但還不確定要不要/怎麼形成 change | `/opsx:explore` | 在 no-stakes、no-artifact 狀態比較 options 與 scope |
| 已有文件，需要找 contradiction、missing case、weak decision | `grill-with-docs` | 對 artifact 做 evidence-based challenge |

這些能力可以串接，但不要同時無差別啟動。先選「主要未知」對應的 lead capability。

### 3.4 Skill Family C — Design and Plan

| Skill | Use When | Primary Output | Gate |
|---|---|---|---|
| **`system-design`** | P3/P2；或 P1 涉及跨 boundary/contract/data、重大 NFR、novel architecture、L2–L3 | System Design Pack、ADRs、Epic/Feature decomposition | System Design Review under Change Gate |
| **`superpowers:brainstorming`** | 新 functionality、behavior change、architecture option、需求仍需釐清 | Approved design/spec、options/trade-offs | Design owner approves direction |
| **`grill-with-docs`** | Design/spec 已形成，需要 adversarial review | Findings + minimal corrections | Material risks/ambiguities closed |
| **`to-tickets`** | P1 Feature / Design 已 approved，需要切成 Sprint-ready delivery slices | P0 tracer-bullet tickets、acceptance、`Blocked by`、execution frontier | 每張 P0 narrow but complete、可獨立驗證；Spike 有 evidence/decision outcome |
| **`superpowers:writing-plans`** | 單一 P0 即將執行，且 multi-step、high-risk 或 complex | JIT executable plan：exact files/interfaces、steps、tests、commands、evidence | Plan 可由沒有背景的 Engineer 執行；無 unresolved design decision |

Planning responsibility：

```text
P1 Feature / Approved Design
→ to-tickets
→ P0 PBI / Story vertical slices + blocking dependencies
→ writing-plans（per P0、JIT、risk/complexity triggered）
→ Execution Layer tasks / plan steps / commits
→ TDD / Implement / Verify
```

- 所有 P0 明確寫 `Blocked by`；沒有 blocker 的項目構成 **execution frontier**。
- Wide refactor 使用 `expand → migrate batches → contract`，每批為可驗證 P0；不要建立一張跨越全程的大 task。
- 不先替整個 Epic 建立巨大 implementation plan。
- 簡單、低風險、單一步驟 P0 可跳過完整 `writing-plans`，但仍保留 acceptance、test direction 與 evidence。

### 3.5 Skill Family D — Implement

| Skill | Use When | Primary Output | Gate |
|---|---|---|---|
| **`superpowers:using-git-worktrees`** | 開始 feature/plan execution，需要隔離 workspace | Isolated worktree + baseline state | Workspace、安全與 baseline tests ready |
| **`superpowers:test-driven-development`** | Feature、bugfix、refactor、behavior change | Red-Green-Refactor evidence + production code | 先看到正確 failure，再看到 pass |
| **`superpowers:executing-plans`** | 已有 plan，需要在另一 session 分批執行 | Completed plan batches + review checkpoints | 每批 plan items 與 evidence completed |
| **`superpowers:subagent-driven-development`** | Plan tasks mostly independent，可在同一 session 分工 | Per-task implementation + spec/quality review | 每 task 通過 review，最後 whole-change review |
| **`superpowers:systematic-debugging`** | Implementation 遇到 failure 或 unexpected behavior | Proven root cause + targeted correction | 不以 random patch 繞過問題 |

### 3.6 Skill Family E — Validate and Finish

| Skill | Use When | Primary Output | Gate |
|---|---|---|---|
| **`superpowers:requesting-code-review`** | Task、feature 或整體 change 完成 | Structured review request + findings | Critical/Important findings closed |
| **`superpowers:receiving-code-review`** | 收到 review feedback | Verified response、fix 或 evidence-based disagreement | Feedback 逐項處理，不盲從也不忽略 |
| **`superpowers:verification-before-completion`** | 宣稱 complete、fixed、tests pass、ready 前 | Fresh command output + requirement checklist | Evidence 支持每項 completion claim |
| **`superpowers:finishing-a-development-branch`** | Implementation/evidence 完成，準備 merge/PR/cleanup | Verified branch disposition | Tests pass、integration choice executed |

### 3.7 Skill Name Governance

Skill name 是 department capability alias；不同 agent/tool 可以有不同 implementation mapping。但對 adoption 而言，不能只列 capability 後讓尚未建立方法的 Engineer 自行摸索。

Department skill policy：

1. **Required discipline**：命中條件時不可省略，例如 unfamiliar brownfield change 先建立 codebase evidence、behavior change 採 test-first discipline、completion claim 前執行 fresh verification。
2. **Golden default skill**：每個 Golden Stage 提供可直接採用的 Department Golden skill/path，作為新手與只會 vibe coding Engineer 的起始標準。
3. **Equivalent mapping allowed**：成熟 Team 可依 approved tool、技術棧與 workflow 使用 equivalent skill，但須在 Skill Registry 證明相同 required input、output、stop condition、gate 與 evidence quality。

因此 `Golden default` 不是唯一工具，但也不是可忽略的隨意建議；未完成 equivalent mapping 時，預設採用 Department Golden skill。

Golden default 的 source、environment、installation、invocation、verification status 與 fallback 由 [`reference/Golden_Skill_Registry.md`](reference/Golden_Skill_Registry.md) 管理。Playbook 擁有 capability 與 execution contract；Registry 擁有 implementation provenance，不在兩處重複維護安裝資訊。

`system-design` 目前是 logical capability bundle，不假設已有同名安裝 skill。沒有 dedicated implementation 時，依序組合 `understand-anything` / `codebase-research`、`/opsx:explore`、`superpowers:brainstorming`、`grill-with-docs`，並由 accountable Architect/Tech Lead 完成 review。

Skill Registry 至少記錄：

| Field | Example |
|---|---|
| Logical capability | `writing-plans` |
| Tool implementation | `superpowers:writing-plans` |
| Supported environments | Claude Code / Codex / other approved agents |
| Owner | Department skill maintainer |
| Source/version | Repository、commit/tag、last verified date |
| Required inputs | Approved design/spec |
| Required outputs | Executable implementation plan |
| Stop condition / gate | Plan executable；無 unresolved design decision |
| Equivalent status | Golden default / approved equivalent / deprecated |

`to-tickets` 是 department delivery-decomposition capability；reference implementation 來自 Matt Pocock `to-tickets`。它在本 Framework 的 default ownership 是 P1 → P0，這是 department policy，不表示外部 skill 只能接受 Feature 作為 input。

`to-tickets` behavior was verified against the official [Matt Pocock skill source](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) on 2026-07-16. Department Work Level ownership and tracker conventions remain authoritative for internal use.

Superpowers names in this Playbook were verified against the official [`obra/superpowers`](https://github.com/obra/superpowers) repository on 2026-07-16. Department rules and local skill versions remain authoritative for internal use.

`writing-plans` behavior was verified against the official [Superpowers skill source](https://github.com/obra/superpowers/blob/main/skills/writing-plans/SKILL.md) on 2026-07-16.

OpenSpec actions and behavior were verified against the official [`Fission-AI/OpenSpec`](https://github.com/Fission-AI/OpenSpec) documentation on 2026-07-16. The command profile installed in each repository remains the execution source of truth.

---

## 4. Universal Stage Cards

### 4.1 Research

**Goal**：建立足夠的 problem、domain、system 與 code understanding，避免直接解錯問題。

| Item | Golden Standard |
|---|---|
| Inputs | Initial request、existing docs、repository、runtime evidence、stakeholder/operator knowledge |
| Golden default skills | 依主要未知選 `understand-anything`、`codebase-research`、`grill-me` 或 `/opsx:explore`；bug/incident 加 `systematic-debugging` |
| Activities | 建立 boundary、flow、facts/assumptions/unknowns、current behavior、impact map；需要 option/scope 探索時先 `/opsx:explore` |
| Minimum artifact | Research Brief / Understanding Summary |
| Gate | Owner 能確認 current state、problem、scope、unknowns 與下一步 |
| Typical existing activities | Intake、backlog refinement、analysis、incident investigation；依 Team workflow調整 |
| Where it normally lives | Existing P3/P2/P1/P0 work item、research attachment/link、architecture knowledge base；durable change 才使用 OpenSpec |
| Decision owner | Product/Engineering Owner；system/domain owner 依 unknown 參與 |
| Additional process required? | Normally no；L2/L3、重大未知或跨 owner handoff 才觸發 review |

`/opsx:explore` 本身不建立 Research Brief；若決定繼續 change，將 material conclusions 帶入 `/opsx:propose` 或正式 Research Brief。

Research Brief minimum fields：

- Problem / opportunity。
- Current behavior and evidence。
- Domain/system boundary。
- Affected users/components/contracts/data。
- Facts / assumptions / unknowns。
- Constraints and non-goals。
- Initial Change Risk Tier / Execution Mode。

### 4.2 System Design

**Goal**：在 implementation planning 前，明確決定 system boundary、responsibilities、interactions 與 operational model，並將 capability 拆成可交付 slices。

System Design trigger：

| Delivery Level | Requirement |
|---|---|
| P3 Product / Program | Required |
| P2 Epic | Required |
| P1 Feature | Cross-boundary/contract/data、重大 NFR、novel architecture 或 L2–L3 時 required |
| P0 PBI / Story | Normally skip；觸及 architecture boundary 時升級處理 |

| Item | Golden Standard |
|---|---|
| Inputs | Approved Research Brief、current/as-is model、constraints、existing architecture/rules |
| Golden default capability/skills | `system-design` bundle：evidence skills → `/opsx:explore` → `superpowers:brainstorming` → `grill-with-docs` |
| Activities | Architecture options、system/component boundaries、runtime/data flow、contracts、NFR、failure/recovery/observability、deployment/operation、decomposition |
| Minimum artifact | System Design Pack；P3/P2 存在 Product/Architecture SSOT，P1 可由 OpenSpec `design.md` 承載 |
| Gate | Accountable Architect/Tech Lead completes System Design Review；它是 Change Gate implementation，不是新 universal gate |
| Typical existing activities | Architecture/RFC review、technical discovery、feature refinement；不要求固定會議名稱 |
| Where it normally lives | Existing architecture SSOT、RFC/ADR；P1 bounded delta 可由 OpenSpec `design.md` 承載 |
| Decision owner | Accountable Tech Lead／Architect，依既有 architecture authority |
| Additional process required? | P3/P2 required、P1 risk-triggered、P0 normally no；只提高既有 review depth，不新增 universal gate |

System Design Pack minimum fields，依 scope/risk 裁剪：

- Goals、non-goals、constraints。
- System context、ownership 與 component boundaries。
- Key runtime interactions and data flows。
- Contracts、data ownership/state model。
- NFR and capacity assumptions。
- Failure、recovery、observability、deployment/operation considerations。
- Selected option、trade-offs 與 ADRs。
- Epic/Feature/Wave decomposition and validation direction。

### 4.3 Feature / Detailed Design

**Goal**：把 Research 與必要的 System Design 轉成 bounded、可實作、可驗證的 target behavior。

| Item | Golden Standard |
|---|---|
| Inputs | Approved Research Brief；System Design triggered 時加 approved System Design Pack/ADRs |
| Golden default skills | `superpowers:brainstorming`；需要 durable change package 時用 `/opsx:propose` 或 `/opsx:new` + `/opsx:continue`；完成後用 `grill-with-docs` |
| Activities | Target behavior/examples、feature boundary、contract/data/state delta、failure behavior、test/rollout direction |
| Minimum artifact | Approved Feature Design / Spec；OpenSpec 採 `proposal + specs + design` |
| Gate | Design owner approves selected approach；material review findings closed |
| Typical existing activities | Refinement、feature design、RFC、design discussion、architecture review when triggered |
| Where it normally lives | Feature/PBI、existing design doc、ADR/RFC、OpenSpec proposal/spec/design |
| Decision owner | Feature/Engineering Owner；material architecture decision 由 Tech Lead/Architect |
| Additional process required? | Normally no separate ceremony；只有 risk/architecture trigger 需要額外 reviewer 或 durable artifact |

Feature/Detailed Design minimum fields：

- Goals / non-goals。
- Target behavior and examples。
- Selected option and trade-offs。
- Component/contract/data changes。
- Failure/recovery/observability behavior when affected。
- Test strategy and acceptance criteria。
- Rollout/migration direction when affected。

### 4.4 Plan

**Goal**：先把 approved Feature 切成可交付的 P0，再於 P0 即將執行時，按風險與複雜度拆成安全的 implementation tasks。

| Planning Depth | Input | Golden Default Skill | Minimum Artifact | Gate |
|---|---|---|---|---|
| **Delivery decomposition** | P1 Feature + Approved Design | `to-tickets` | P0 PBI/Story tracer bullets + acceptance + `Blocked by` | 每張 P0 narrow but complete、Sprint-ready、可獨立驗證；frontier 可開始 |
| **Implementation planning** | 單一即將執行的 P0 + repository context | Triggered `superpowers:writing-plans`；OpenSpec `tasks.md` 可承載 | Exact files/interfaces/tests/commands 的 executable plan | 每個 task 可獨立理解、test、review；無 unresolved design decision |

Typical existing integration：delivery decomposition 通常發生於 backlog refinement／iteration planning，P0 set 與 `Blocked by` 留在 tracker；JIT implementation plan 通常留在單一 P0、OpenSpec `tasks.md`、PR description 或 linked plan。Product/Engineering Owner 對 P0 outcome/dependency accountable，Change Owner 對 executable plan accountable。正常情況不新增 planning ceremony；只有 dependency、risk 或 design ambiguity 需要既有 owner/reviewer 介入。

Delivery decomposition rules：

- Slice by end-to-end behavior，不按 layer/component 產生「先 DB、再 API、再 UI」的水平 tickets。
- 每張 P0 明確列出 `Blocked by`；沒有 blocker 的 P0 是 execution frontier。
- Wide refactor 使用 `expand → migrate batches → contract`；migration batches 各自可驗證。
- P3/P2 先拆到 P1；不要替整個 Epic 建立一份 implementation plan。

Implementation planning 採 **just-in-time**。簡單、低風險、單一步驟 P0 可用 inline plan，跳過完整 `writing-plans`。需要完整 plan 時，每個 task 至少包含：

- Goal and scope。
- Exact files / interfaces。
- Expected behavior。
- Failing test or verification first。
- Minimal implementation steps and commands。
- Completion evidence。
- Dependency on previous/next tasks。

若 OpenSpec `tasks.md` 已達相同標準，直接作為 SSOT；**不建立雙份 plan**。

### 4.5 Implement

**Goal**：依 plan 小步完成 change，不擴張 scope，持續產生 evidence。

| Item | Golden Standard |
|---|---|
| Inputs | Approved plan、isolated workspace、baseline tests |
| Golden default skills | OpenSpec change 先 `/opsx:apply`；執行紀律使用 `using-git-worktrees` → `test-driven-development` → `executing-plans` 或 `subagent-driven-development` |
| Activities | Red-Green-Refactor、small commits、per-task self-review、unexpected failure root-cause analysis |
| Minimum artifact | Code/config/migration + tests + execution ledger |
| Gate | 每個 task 通過 plan compliance 與 targeted verification |
| Typical existing activities | Development、branch、migration/configuration preparation、pairing |
| Where it normally lives | P0/Task、branch、commits、code/config、test output；OpenSpec change 只在已採用時更新 |
| Decision owner | Change Owner；reviewer 對 accepted diff 仍負責 |
| Additional process required? | Normally no；沿用 existing development controls，L2/L3 依 risk 增加 review/segmentation |

Execution choice：

| Situation | Use |
|---|---|
| Small feature/task、單一 Engineer/session | Direct TDD execution |
| Multi-task plan、tasks mostly independent、同一 session | `subagent-driven-development` |
| Approved plan 交給另一 session 分批執行 | `executing-plans` |
| Failure/root cause unknown | 暫停 random patch，改用 `systematic-debugging` |

### 4.6 Validate

**Goal**：用 fresh evidence 證明 requirement、risk、quality 與 completion，而不是相信 agent summary。

| Item | Golden Standard |
|---|---|
| Inputs | Actual diff、plan、acceptance criteria、test outputs、risk profile |
| Golden default skills | `requesting-code-review`、`receiving-code-review`、`verification-before-completion`；Expanded OpenSpec 加 `/opsx:verify` |
| Activities | Spec compliance、code quality、risk-focused tests、requirement checklist、branch completion |
| Minimum artifact | Validation Record / PR evidence |
| Gate | Material findings closed；completion claims 均有 fresh evidence |
| Typical existing activities | PR/MR review、pipeline、test/staging、release readiness、post-deploy observation |
| Where it normally lives | PR/MR、pipeline/test report、release/change record、dashboard；reference existing evidence |
| Decision owner | Change Owner + Reviewer；environment/production decision 仍由 Release/Service Owner |
| Additional process required? | L0/L1 可在 ticket/PR 自證；L2/L3 依既有 test/release governance 增加 independent evidence/approver |

Validation 必須分兩層：

1. **Task/Feature Verification**：behavior、tests、diff、plan compliance。
2. **Risk Verification**：contract、data、NFR、failure/recovery、operability 等 affected qualities。

完成後再使用 `finishing-a-development-branch` 進入 merge/PR/cleanup decision；OpenSpec change 在 evidence 與 release decision ready 後執行 `/opsx:sync` 與 `/opsx:archive`。

---

## 5. P3 Playbook — Greenfield Product

### 5.1 Objective

從模糊機會建立可交付 product direction、architecture runway 與可驗證 MVP，並拆成 Epics/Features；不得直接用一份大型 prompt 產生完整 product。

### 5.2 Golden Flow

| Stage | Golden Default Skills | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | `grill-me`、`understand-anything`、`/opsx:explore` | Problem、users/workflow、domain、constraints、success metrics、unknowns、options | Product Research Brief、Domain/Workflow Map | Product/Engineering Owner confirms problem and boundary |
| Design | `system-design` bundle、`brainstorming`、`grill-with-docs` | Product/domain design → system context、boundaries、runtime/data、NFR、operating model、MVP architecture | Product/Domain Design、System Design Pack、initial ADRs | Product approval + System Design Review |
| Plan | Portfolio decomposition / roadmap planning | MVP scope、Epic map、dependency order、architecture runway、validation plan；不建立 program-level implementation plan | Product Roadmap、Epic Backlog、MVP Evidence Plan | Roadmap decomposable into P2 Epics |
| Implement | P2/P1/P0 playbooks | Build vertical slices；每個 Epic/Feature 走自己的 Golden Flow | Working increments、tests、decision/evidence ledger | Per-Epic/Feature gates |
| Validate | code review、verification、product evidence | User/business acceptance、architecture conformance、NFR、operational readiness | MVP/Product Validation Report | Product Owner + Service Owner go/no-go |

**OpenSpec scope rule**：P3 direction、product architecture 與 roadmap 使用產品/架構 SSOT；不要建立一個涵蓋整個 product 的巨型 OpenSpec change。Change container 只承載 coherent P1 Feature 或需要 durable agreement 的 P0 PBI。

### 5.3 Minimum Product Artifact Pack

- Product Charter / Opportunity Brief。
- Domain and User Workflow Map。
- System Context and Ownership Boundary。
- Product/Domain Design。
- System Design Pack + NFR profile + key ADRs。
- MVP scope and Epic Map。
- Validation/learning plan。
- Release/operation ownership。

### 5.4 Greenfield Gates

#### Product Understanding Gate

- Problem、target users/workflow、business outcome 清楚。
- Domain concepts、constraints、unknowns 可見。
- MVP 是 learning slice，不是功能清單堆疊。

#### Product and System Design Gate

- Boundary、data ownership、integration、NFR 與 operating model 清楚。
- Architecture runway 足以支持 MVP，但沒有過度設計未來。
- Epics 可以各自產生 working, testable increment。

#### Product Evidence Gate

- MVP outcome、quality guardrails 與 operational readiness 有 evidence。
- Learning 已回饋 roadmap，不以「完成全部需求」取代 product validation。

---

## 6. P3 Playbook — Legacy Modernization / Migration

### 6.1 Objective

在不失去 hidden behavior、domain rules 與 production safety 的前提下，逐步改變 legacy architecture、technology 或 deployment model。

### 6.2 Golden Flow

| Stage | Golden Default Skills | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | `understand-anything`、`codebase-research`、`grill-me`、`/opsx:explore`、`systematic-debugging` | As-is behavior、entry points、dependencies、data、operations、incidents、hidden rules、migration options | As-Is System Model、Behavior Catalog、Dependency/Data Map、Unknowns | Domain + Legacy Owner confirms model |
| Design | `system-design` bundle、`brainstorming`、`grill-with-docs` | Target System Design、seams/strangler、compatibility、migration/data strategy、failure/recovery | Target System Design Pack、Migration Strategy、Compatibility Contract、ADRs | System Design Review + Service Owner approval |
| Plan | Migration roadmap / wave decomposition | Characterization baseline、migration waves、parallel run、cutover/rollback、Epic/Feature breakdown；不建立跨 waves implementation plan | Modernization Roadmap、Wave Plans、Parity/Evidence Matrix | Each wave bounded and recoverable |
| Implement | worktree、TDD、executing/subagent-driven development | Characterization first、incremental replacement、dual-run/adapters when needed | Migrated slices、tests、reconciliation evidence | Per-wave compliance and quality review |
| Validate | review、verification-before-completion | Behavior parity/correction、performance、data reconciliation、failure/recovery、cutover rehearsal | Migration Validation Record、Cutover Readiness | Domain + Service Owner go/no-go |

**OpenSpec scope rule**：不要把多年 modernization roadmap 或整個 wave 塞進單一 change folder。Wave 由 roadmap/architecture artifacts 管理；其 coherent P1 Feature 或需要 durable agreement 的 P0 PBI 各自使用 bounded Change container。

### 6.3 Minimum Modernization Artifact Pack

- As-Is Architecture / Runtime / Data Flow。
- Behavior and Domain Rule Catalog。
- Characterization Test Baseline。
- Dependency、Interface、Data Ownership Map。
- Target System Design Pack、ADRs and Migration Principles。
- Compatibility / Parity Definition。
- Migration Waves and Exit Criteria。
- Cutover、Rollback/Recovery、Observation Plan。

### 6.4 Modernization Non-Negotiables

1. **No modernization before behavior understanding.**
2. **Characterization before structural replacement.**
3. **每一 wave 必須有 independent value/evidence/recovery boundary。**
4. 已知 legacy bug 必須明確決定 `preserve`、`correct` 或 `defer`。
5. Technical migration 完成不等於 production migration 完成；data、operation、support ownership 必須一起移轉。

---

## 7. P2 Playbook — Epic

### 7.1 Objective

將完整 business/technical capability 轉成 coherent architecture delta、Feature Map 與可逐步 release 的 delivery slices。

### 7.2 Golden Flow

| Stage | Golden Default Skills | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | `understand-anything`、`codebase-research`、`grill-me` | Capability outcome、affected systems/contracts/data、dependency、NFR、unknowns | Epic Research Brief、Impact Map | Epic Owner confirms outcome/scope |
| Design | `system-design` bundle、`brainstorming`、`grill-with-docs` | End-to-end flow、System Design/architecture delta、contracts、feature boundaries、failure modes | Epic System Design Pack、Feature Map、ADRs | System Design Review by Tech Lead/Architect |
| Plan | Feature decomposition / delivery planning | Sequence Features、integration milestones、test/release strategy；不建立 Epic implementation plan | Epic Delivery Plan、Feature Backlog、Integration Evidence Plan | Features independently testable/releasable |
| Implement | P1/P0 playbooks | Execute each Feature；maintain contract/integration ledger | Feature increments、contract tests | Feature gates + periodic Epic review |
| Validate | code review、verification | End-to-end capability、contract compatibility、NFR、rollout readiness | Epic Validation Record | Epic Owner accepts capability |

**OpenSpec scope rule**：Epic Design/Feature Map 管方向；OpenSpec Change 不作為 Epic hierarchy level。每個 coherent P1 Feature，或需要 durable agreement 的 P0 PBI，使用自己的 scoped change。

### 7.3 Epic Minimum Artifact Pack

- Epic Brief：Outcome、scope、non-goals、success metrics。
- Affected System / Contract / Data Map。
- Epic System Design Pack / Architecture Delta + ADRs。
- Feature Map and dependency order。
- Integration/NFR/rollout evidence plan。
- Epic acceptance and release record。

### 7.4 Epic Decomposition Test

每個 Feature 必須：

- 有獨立 outcome 或 learning value。
- 有自己的 acceptance criteria。
- 可在有限 context 內 design/plan/review。
- 不依賴其他全部 Features 完成才可驗證。
- 清楚說明 shared contract 與 integration dependency。

如果 Feature 仍需要同時修改大量無關 subsystems，Epic decomposition 尚未完成。

---

## 8. P1 Playbook — Feature

### 8.1 Objective

完成可獨立驗收、部署或控制的 bounded behavior change。這是工程師最常使用的完整 Golden Flow。

### 8.2 Golden Flow

| Stage | Golden Default Skills | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | `codebase-research`；模糊時 `/opsx:explore`；必要時 `grill-me` / `understand-anything` | Current behavior、existing pattern、impact、acceptance、risk、options | Feature Research Brief / ticket context | Owner confirms problem and boundary |
| Design | Triggered 時先 `system-design`；再 `/opsx:propose` + `brainstorming` quality、`grill-with-docs` challenge | System boundary/architecture delta when triggered；target behavior、contracts/data/failure、test strategy | Triggered System Design Pack/ADR + Proposal + Specs + Design | System Design Review when triggered；Feature Design approved |
| Plan | `to-tickets` | Slice approved Feature into P0 tracer bullets；acceptance、`Blocked by`、execution frontier；wide refactor 用 expand/migrate/contract | P0 PBI/Story Backlog + Dependency Graph | 每張 P0 narrow but complete、Sprint-ready、可獨立驗證 |
| Implement | P0 Playbook；各 frontier P0 按需 `writing-plans` 後 TDD/execution | 逐張 P0 Red-Green-Refactor、small commits、per-task checks | P0 increments + tests + updated ticket/task state | Per-P0 reviews pass |
| Validate | P0 evidence rollup、code review、verification-before-completion、risk-based `/opsx:verify` | Aggregate Feature acceptance、artifact alignment、tests、affected risk qualities | Feature Validation Record | Reviewer + Owner accept Feature evidence；then sync/archive |

### 8.3 Feature Golden Artifact Pack

最小可放在同一個 ticket/design/PR chain：

1. **Feature Brief**：Goal、scope/non-goals、current/target behavior、acceptance criteria。
2. **System Design when triggered**：boundary、architecture delta、contracts/data/runtime、NFR、ADRs。
3. **Feature Design**：selected approach、affected behavior/data/failure、test direction。
4. **P0 Backlog**：tracer-bullet slices、acceptance criteria、`Blocked by`、execution frontier。
5. **Change**：由各 P0 產生的 reviewable code/config/tests。
6. **Validation**：requirement checklist、fresh test output、review findings、residual risk。

### 8.4 Lightweight vs Full Feature Flow

| Condition | Flow |
|---|---|
| Existing pattern、single component、L1 risk | Research/Design 可合併成短 Feature Brief；仍需 P0 slice、tests、review；若 Feature 本身已是最小 vertical slice，可只產生一張 P0 |
| Cross-boundary/contract/data、重大 NFR、novel architecture 或 L2+ | Trigger System Design；separate Research、System/Feature Design、Plan artifacts；independent review |
| Critical control path、L3 risk | System Design Review + domain/architecture review、Evidence Portfolio、release/recovery readiness |

---

## 9. P0 Playbook — PBI / User Story

### 9.1 Objective

完成可進 Sprint、narrow but complete、可獨立驗證的 vertical slice，不把簡單 P0 變成文件專案，也不因 slice 小就跳過理解與 evidence。

P0 可為 User Story、Engineering Story / Enabler、Bug 或 Spike。開始前確認：

- 有獨立 outcome／learning 與 acceptance evidence。
- 不需要其他全部 P0 完成才可驗證。
- Scope 能在 bounded context 中 design、implement、review。
- `Blocked by` 已明確；沒有 blocker 時屬於 execution frontier。

### 9.2 Standard P0 Flow

```text
Targeted Research → Micro-design → Micro-plan → TDD Change → Fresh Verification
```

| Stage | Default Skill | Minimum Output |
|---|---|---|
| Research | `codebase-research` | Affected files/behavior、existing pattern、risk |
| Design | Short `brainstorming` when behavior changes | Selected approach + must-not-change |
| Plan | 單一步驟 P0 用 inline plan；multi-step/high-risk/complex P0 用 JIT `writing-plans` | Exact steps、files/interfaces、tests、commands |
| Implement | `test-driven-development` | Failing test → minimal change → pass |
| Validate | code review as required + `verification-before-completion` | Fresh targeted/full test evidence |

P0 不預設要求 OpenSpec。若 P0 涉及 durable behavior agreement、多人 handoff 或需長期維護的 spec，可建立 **P0-scoped** OpenSpec Change；若實際 scope 改變 architecture boundary 或已不是單一 vertical slice，才重新分類為 P1/P2。純 mechanical L0/L1 P0 可直接使用 ticket + PR evidence。

### 9.3 Bug / Incident Variant

```text
Reproduce → Systematic Debugging → Root Cause → Regression Test → Minimal Fix → Verify
```

Minimum evidence：

- Observed symptom and reproduction。
- Facts vs hypotheses。
- Proven root cause。
- Regression test that fails before fix and passes after fix。
- Scope check：為何不需要 broader change。
- Detection/operability improvement when applicable。

Incident review 完成時，至少沉澱：

- Incident Timeline。
- Proven Root Cause。
- Corrective/Preventive Action Items 與 owners。
- Updated Runbook / Alarm / Test（依 incident gap）。

### 9.4 Engineering Story / Enabler and Refactor Variant

- 先確認 behavior-preserving 或 behavior-changing。
- Behavior-preserving：existing/characterization tests 先建立 baseline。
- 小型 behavior-preserving refactor 可是一張 P0 Engineering Story / Enabler；仍需可驗證 outcome。
- Wide refactor：切成 `expand → migrate batches → contract` 的 P0 sequence，每張標示 `Blocked by`；不要用一張大 task 橫跨全程。
- Behavior-changing：依 outcome 重新分類為 P0 User Story 或 P1 Feature，不以 refactor 名義隱藏功能變更。
- 不混入 unrelated formatting、dependency upgrades 或 architecture redesign。

### 9.5 Spike Variant

- 必須 time-boxed，並明確寫出要降低的 unknown/risk。
- Output 是 evidence、option comparison、prototype result 或 decision recommendation，不是「研究過了」。
- Completion 以可重現的 commands/data/findings 與 decision owner 驗證。
- 若確認要做 production change，另形成 P1 Feature 或 P0 PBI；Spike 本身不偷渡 implementation。

---

## 10. Skill Selection Matrix

### 10.1 Stage × Skill

這張 Matrix 是 Department Golden default registry。`Primary` 表示該情境的預設安全路徑，不代表每個 work item 都要跑該列；由 Six Golden Questions 與 Trigger Rules 選出下一個 skill。沒有 approved equivalent mapping 的 Engineer／Team 直接採用本表 defaults。

| Skill | Research | Design | Plan | Implement | Validate |
|---|:---:|:---:|:---:|:---:|:---:|
| understand-anything | Primary for broad/unfamiliar context | Support |  |  |  |
| codebase-research | Primary for existing systems | Support evidence | Support file map | Support pattern lookup | Support traceability |
| grill-me | Primary for tacit knowledge | Support decisions |  |  |  |
| `/opsx:explore` | Primary for no-stakes option/scope exploration | Handoff only |  |  |  |
| `/opsx:propose` or `new/continue/ff` | Research inputs | Primary durable agreement | Durable task/ticket references |  | Alignment reference |
| grill-with-docs | Review research | Primary design challenge | Review plan when high risk |  | Review evidence/doc consistency |
| system-design | Evidence inputs | Primary for P3/P2 and triggered P1 | Architecture/decomposition handoff | Conformance reference | Architecture conformance evidence |
| brainstorming | Scope/problem exploration | Primary | Handoff to `to-tickets` |  |  |
| `to-tickets` |  | Approved design input | Primary for P1 → P0 | Delivery contract | P0 acceptance rollup |
| writing-plans |  |  | Triggered per P0, JIT | Execution contract | Plan compliance check |
| systematic-debugging | Primary for incidents/bugs | Root-cause-informed design | Targeted fix plan | Failure handling | Reproduction verification |
| test-driven-development |  | Test strategy | TDD task steps | Primary | Red-Green evidence |
| executing-plans / subagent-driven-development |  |  | Read approved plan | Primary for multi-task work | Completion ledger |
| `/opsx:apply` |  |  | Reads tasks | OpenSpec execution entry | Task/artifact alignment |
| requesting/receiving-code-review |  |  |  | Per-task review | Primary |
| verification-before-completion |  |  |  | Per-task claims | Mandatory before completion claim |
| `/opsx:verify` |  |  |  |  | Expanded artifact/implementation verification |
| `/opsx:sync` + `/opsx:archive` |  |  |  |  | Update durable truth and close change |
| finishing-a-development-branch |  |  |  |  | After validation |

### 10.2 Trigger Rules

| If… | Use… |
|---|---|
| 不知道系統全貌或 domain language | `understand-anything` |
| 知道需求，但不知道 code 在哪裡、如何流動 | `codebase-research` |
| 重要規則在使用者/operator 腦中 | `grill-me` |
| 有 problem，但還沒有 plan；需要比較 options/scope | `/opsx:explore` |
| 已清楚要做什麼，需要 durable why/what/how/steps agreement | `/opsx:propose`；複雜工作用 `new/continue` |
| 已有文件但不確定是否完整/一致 | `grill-with-docs` |
| P3/P2；或 P1 涉及跨 boundary/contract/data、重大 NFR、novel architecture、L2+ | `system-design` bundle，完成 System Design Review |
| 要新增或改變 behavior | `brainstorming`，design approved 後才能 plan/implement |
| P1 Feature / Approved Design 要切成 Sprint-ready vertical slices | `to-tickets`；每張 P0 標示 `Blocked by` |
| 單一 P0 即將執行，且 multi-step、high-risk 或 complex | `writing-plans`；簡單單一步驟 P0 可 inline |
| 寫 feature/bugfix/refactor code | `test-driven-development` |
| 遇到不明 failure | `systematic-debugging`，停止 random fixes |
| Plan 有多個 tasks | 選 `executing-plans` 或 `subagent-driven-development` |
| 準備說「完成、修好、tests pass」 | `verification-before-completion` |
| OpenSpec implementation 與 artifacts 需要一致性檢查 | `/opsx:verify` |
| Change 已驗證，需要更新 specs/source of truth | `/opsx:sync` → `/opsx:archive` |

---

## 11. Golden Gates by Delivery Level

| Level | Understanding Gate | System/Feature Design + Plan Gate | Evidence Gate |
|---|---|---|---|
| P3 Product/Program | Product/domain/as-is context 與 decomposition basis 清楚 | System Design Review complete；architecture/roadmap/waves 可拆成 Epics | Product/Migration outcome、NFR、operation/cutover ready |
| P2 Epic | Capability、impact、dependency 與 NFR 清楚 | System Design Review complete；architecture delta、contracts、Feature Map 可執行 | E2E capability、integration、NFR、rollout ready |
| P1 Feature | Current/target behavior、scope、risk 清楚 | Triggered 時完成 System Design Review；Feature Design approved；P0 slices 與 blockers 可執行 | Feature acceptance、P0 evidence rollup、affected risk evidence |
| P0 PBI / Story | Outcome、acceptance、affected behavior 與 dependency 清楚 | Micro-design + JIT/inline plan + test direction | Fresh acceptance/test/review evidence |

System Design Review 是 Change Gate 的 risk-based implementation，不是第四個 universal gate。Gate 通過不代表要開會；evidence 已存在 architecture/design review、ticket、PR 或 pipeline 時直接引用。

---

## 12. Department Golden Artifact Map

| Artifact | P3 | P2 | P1 | P0 |
|---|:---:|:---:|:---:|:---:|
| Research / Understanding Brief | Full | Required | Required, can be inline | Lightweight |
| Domain / As-Is System Model | Required by archetype | When affected | Reference | Not normally required |
| System Design Pack | Required: product/target architecture | Required: architecture delta | Trigger-based | Not normally required |
| Approved Feature / Detailed Design | Per Epic/Feature | Per Feature | Required | Micro-design when behavior changes |
| OpenSpec Change Container | Not at P3; child P1/P0 only | Not Epic hierarchy; child P1/P0 only | Default when durable agreement matters | Optional when agreement/handoff matters |
| Decomposition | Epic/Wave Map | Feature Map | P0 tickets + `Blocked by` | Execution tasks / plan steps |
| Implementation Plan | None at this level | None at this level | Not Feature-wide; JIT per P0 | Triggered for multi-step/risky/complex；inline for simple |
| Tests / Executable Evidence | Strategy + rollup | Integration/NFR rollup | Feature tests | Targeted tests |
| Review Record | Product/architecture decisions | Epic/design review | PR review | Risk-based review |
| Release / Migration Evidence | Required | Required when released | Required when deployed | Existing process |

**Document minimization rule：同一 artifact 可以同時滿足多個欄位；不要為了表格完整建立空文件。**

### 12.1 Reference Tracker Mapping

| Framework | Azure DevOps | GitLab |
|---|---|---|
| P3 Product / Program | Portfolio / Roadmap context | Top-level Epic / Group Roadmap |
| P2 Epic | Epic | Epic |
| P1 Feature | Feature | Child Epic，或 team convention `type::feature` |
| P0 PBI / Story | PBI / User Story / Bug | Issue；story / enabler / bug / spike type 或 label |
| Execution Layer | Task | Task child item 或 checklist |
| Implementation | Branch / PR / Commit | Merge Request，連回 P0 Issue |
| Release / Sprint | Existing release/sprint construct | Milestone / Iteration |

GitLab Milestone／Iteration 是 planning dimension，不是 hierarchy level。Azure DevOps Bug placement 與 GitLab types/labels 可能依 process/version/configuration 不同；只要保留 Framework semantics 即可，不反向讓 tracker 重定義 Work Level。

Reference：Azure DevOps [Define features and epics](https://learn.microsoft.com/en-us/azure/devops/boards/backlogs/define-features-epics?view=azure-devops) / [About work items](https://learn.microsoft.com/en-us/azure/devops/boards/work-items/about-work-items?view=azure-devops)；GitLab [Child items](https://docs.gitlab.com/user/work_items/child_items/) / [Milestones](https://docs.gitlab.com/user/project/milestones/)。

### 12.2 Artifact Placement — Information, Not File Format

**Artifact requirement defines required engineering information and evidence, not a mandatory file format.**

| Information / Evidence | Reuse First |
|---|---|
| Problem、scope、acceptance、risk、P0 type | Existing Epic／Feature／PBI／Issue |
| Research/system understanding | Work item attachment/link、architecture knowledge base、repository guidance |
| Durable change/design agreement | Existing design/RFC/ADR；OpenSpec when adopted and longevity requires it |
| P0 slices、blockers、frontier | Existing backlog/tracker |
| Per-P0 execution plan | P0/Task、OpenSpec `tasks.md`、PR description or linked plan |
| Diff、review、tests | PR/MR、pipeline、test report |
| Release/E3 authorization | Release ticket、change request、deployment record |
| Runtime/incident learning | Dashboard、runbook、post-incident review、follow-up backlog |

Placement rules：reuse existing system of record；avoid duplication；reference rather than copy；只有 risk、scale、longevity 或跨人 handoff 需要時才提高 formality。

### 12.3 Team-owned Workflow Adapter and Templates

Department 定義 Golden Stage contract、minimum required information、quality criteria、risk-triggered additions 與 traceability。每個 Team 自主定義：

- Local activity → Golden Stage／Gate mapping。
- Tracker fields、Team templates 與 repository instructions。
- Technology-specific validation checklist、product DoD 與 domain constraints。
- Local examples、prompts／skills 與 artifact placement。

Team template 可以不同，但不能省略對應 risk level 的 minimum information、decision responsibility 與 evidence。這個 adapter 讓 Playbook 進入 Team 既有 operating model，而不是要求 Team 離開現有流程。

---

## 13. Engineer Quick Starts

### Scenario A —「我要做一個新 Feature」

```text
codebase-research
→ /opsx:explore (if fuzzy)
→ system-design + System Design Review (if triggered)
→ /opsx:propose
→ grill-with-docs (risk-based)
→ to-tickets: P0 slices + Blocked by
→ each frontier P0: writing-plans if triggered
→ /opsx:apply + worktree + TDD + execute tasks
→ code review + verification-before-completion
→ /opsx:sync → /opsx:archive
```

### Scenario B —「我要修一個 Bug」

```text
reproduce
→ systematic-debugging
→ regression test
→ confirm P0 acceptance + Blocked by
→ inline plan, or writing-plans if multi-step/complex
→ minimal fix with TDD
→ review
→ verification-before-completion
```

### Scenario C —「我要開一個 Greenfield Product」

```text
grill-me + understand-anything
→ product/domain research + /opsx:explore
→ product/domain design
→ system-design bundle + grill-with-docs
→ epic map / MVP plan
→ each P1 Feature follows Design → to-tickets → P0 execution
→ scoped OpenSpec Change only at coherent P1/P0
```

### Scenario D —「我要做 Legacy Modernization / Migration」

```text
understand-anything + codebase-research + grill-me
→ as-is model + behavior catalog + characterization baseline
→ /opsx:explore migration options
→ target system-design + migration design
→ grill-with-docs + System Design Review
→ wave plan
→ each wave decomposes to P1 Features, then expand/migrate/contract P0 slices
→ scoped OpenSpec Change only where P1/P0 durable agreement is needed
→ parity/reconciliation/cutover validation
```

### Scenario E —「需求不清楚，但主管要我快點做」

```text
grill-me
→ define problem/scope/success
→ codebase-research if existing system
→ /opsx:explore
→ owner confirms direction
→ /opsx:propose
```

快不是跳過 Research/Design；快是使用正確 skill，把模糊與 rework 提前消除。

### Scenario F —「我要寫 RFC / Architecture Decision」

```text
understand-anything + codebase-research (for brownfield)
→ /opsx:explore options
→ system-design or brainstorming by scope
→ grill-with-docs
→ approved proposal/spec/design + ADR
```

Minimum pack：Context Summary、Current State、Problem Statement、Alternatives/Trade-offs、Grill Result、ADR/Design Decision。

### Scenario G —「我要做 Incident Review 並防止再發」

```text
understand-anything + systematic-debugging
→ timeline + proven root cause
→ grill-with-docs on incident evidence/runbook
→ corrective actions
→ updated test/alarm/runbook
→ verification-before-completion
```

### Scenario H —「我要設計新系統或跨系統 Capability」

```text
understand-anything + codebase-research (for brownfield)
→ Research Brief / Current System Model
→ /opsx:explore architecture options
→ system-design capability bundle
→ grill-with-docs
→ System Design Review
→ ADRs + Epic/Feature Map
→ approved P1 Features use to-tickets; P0 uses JIT planning when triggered
```

Minimum System Design Pack：System Context、boundaries/ownership、runtime/data flow、contracts、NFR、failure/recovery/observability、deployment/operation considerations、ADRs、decomposition。

---

## 14. Manager and Tech Lead Usage

Manager / Tech Lead 不需要 review 每個 prompt，只需在適當 level 看 artifacts 與 gates：

| Role | Primary Review |
|---|---|
| Manager / Product Owner | Outcome、scope、priority、success metrics、delivery decomposition |
| Senior / Tech Lead | Research quality、design choice、plan boundaries、evidence coverage |
| Architect | P3/P2 architecture、contracts、data ownership、NFR、migration/recovery |
| Service Owner / SRE | Release、observability、capacity、failure/recovery、operation ownership |
| Engineer | Actual understanding、plan、change、tests、review closure |

Manager 應問：

1. Work Level 與 Archetype 選對了嗎？
2. Current Stage 是什麼，minimum artifact 在哪裡？
3. System Design 是否 required/triggered？若是，System Design Review 在哪裡？
4. 下一個 Human Gate 是誰？
5. Change Risk 與 AI Execution Mode 是否相稱？
6. P1 的 P0 slices、`Blocked by` 與 execution frontier 是否清楚？
7. 有什麼 evidence，還有哪些 unknowns？

---

## 15. Anti-Overprocessing Rules

1. **不要每個 P0 都跑全部 skills。** 只使用當前 stage 的 Golden default skill 與必要 supporting skill；已完成 equivalent mapping 的 Team 可使用等價 skill。
2. **不要用 `writing-plans` 補救沒有 approved design 或 P0 slicing。** 前者回到 Research/Design，後者先用 `to-tickets`。
3. **不要用 brainstorming 取代 codebase evidence。** Existing system 先做 codebase research。
4. **不要用大量文件取代 decision。** Artifact 必須服務 handoff、review 或 evidence。
5. **不要因 P3 就一次設計所有 Features。** 先建立 product/epic boundaries，逐層展開。
6. **不要因 P0 就跳過 root cause 或 tests。** 深度可以輕，閉環不能消失。
7. **不要讓 skill workflow 取代現有 SDLC authorization。** E3 actions 仍由既有 owner/process 控制。
8. **不要讓 OpenSpec 與 skill workflow 產生雙份 design/plan。** OpenSpec artifacts 是 durable SSOT；其他 skills 提供建立與 review 的品質方法。
9. **不要在 Explore 裡偷偷 implementation。** `/opsx:explore` 維持 E0；確認 change intent 後才進 proposal/change package。
10. **不要把 System Design 變成所有工作的 mandatory ceremony。** P3/P2 required；P1 risk-triggered；P0 通常使用 micro-design。
11. **不要複製 architecture SSOT。** P3/P2 System Design 存在既有 Product/Architecture artifact；OpenSpec 只引用或記錄 bounded delta。
12. **不要先替整個 Epic 建立 implementation plan。** 先拆 Features，再用 `to-tickets` 切 P0；`writing-plans` 只在單一 P0 即將執行時觸發。
13. **不要把 Task 或 OpenSpec Change 當成 P0 同義詞。** Task 位於 Execution Layer；Change 是 P1/P0 scope-dependent container。
14. **不要建立平行 AI SDLC。** Golden Stage 要 mapping 到既有 backlog、design、PR、test、release 或 incident flow，不是再開一條 process。
15. **不要把 Golden Stage 固定成 Team 統一 phase。** 一個 activity 可承載多個 Stages；一個 Stage 也可跨 activity／Sprint。
16. **不要由 Department 統一所有 Team templates。** Department 定 contract/quality bar；Team 定格式、欄位與 local workflow。
17. **不要忽略既有十個以上 pilots，重新要求證明。** 先 consolidation、選 canonical cases，其餘進 Case Library。

---

## 16. Agile / Sprint Integration and Definition of Ready / Done

Sprint／Iteration 是 Team planning dimension，不是 Golden Stage boundary。Research、Design 與 Validate 可以在同一 Sprint、以前置 Spike、Feature-level work 或 cross-Sprint activity 出現；Playbook 不強迫所有工作用相同切割方式。

P0 進 Sprint／Iteration 的 minimum Definition of Ready：

- Clear outcome。
- Acceptance criteria。
- Known dependencies／`Blocked by`。
- Appropriate change boundary。
- Initial Change Risk Tier／Execution Mode。
- Enough understanding to begin safely。

P0 完成的 minimum Definition of Done：

- Acceptance criteria verified、required tests passed。
- Material review findings resolved。
- Documentation／contract／runbook updated when applicable。
- Release and operational evidence appropriate to risk。
- Residual risk and next owner visible。

以下 stage readiness 用來找出下一個缺口，不是額外 Sprint status 或 mandatory checklist。

### Ready for Research

- Initial request / problem signal 存在。
- Owner 與主要 evidence sources 可識別。

### Ready for Design

- Current state、problem、scope、unknowns 有足夠 understanding。
- Blocking domain/codebase ambiguity 已解決或有明確 decision owner。

### Ready for Plan

- System Design triggered 時，System Design Pack/ADRs 與 review 已完成。
- Feature/Detailed Design/spec approved。
- Contracts、data/state、failure behavior、acceptance/test direction 清楚。
- P1 delivery planning 準備使用 `to-tickets`；P0 implementation planning 必須先有一張明確 P0。

### Ready for Implement

- P0 outcome、acceptance、`Blocked by` 與 execution readiness 清楚。
- Triggered 時，單一 P0 的 JIT plan bounded and executable；簡單 P0 有 inline steps/test direction。
- Workspace/baseline ready。
- AI Execution Mode 與 authorization 清楚。

### Ready for Validate

- Planned tasks complete。
- Actual diff、tests、deviations、remaining risks 可見。

### Done

- Acceptance criteria 有 fresh evidence。
- Material review findings closed。
- Affected risk qualities 已驗證。
- 若使用 OpenSpec Change，已在適當時點 sync/archive；未使用時 ticket/PR chain 已足以承載 agreement 與 evidence。
- Release/operation handoff ready when applicable。
- 下一個 owner 不需依賴原始 chat 才能接手。

---

## Appendix A — Reference Work Brief Contract

此格式是 reference pattern，不是 Department mandatory template。Team 可把相同 minimum information 放入既有 tracker、OpenSpec、design doc 或 PR，並維護自己的 template。

```markdown
# Work Brief

## Classification
- Delivery Level: P3 / P2 / P1 / P0
- P0 Type: User Story / Engineering Story-Enabler / Bug / Spike / N/A
- Blocked by: ticket IDs / None
- Archetype: Greenfield / Modernization-Migration / Standard
- Change Risk Tier: L0 / L1 / L2 / L3
- AI Execution Mode: E0 / E1 / E2 / E3
- System Design: Required / Triggered / Not Required; reason

## Goal and Outcome

## Current Context / Evidence

## Scope / Non-goals / Constraints

## Acceptance Criteria

## Current Stage, Required Capability and Golden Default Skill

## Expected Artifact and Human Gate
```

## Appendix B — Reference Validation Record Contract

此格式是 reference pattern；若 PR、pipeline、test report、release record 或 dashboard 已承載相同 evidence，直接 reference，不建立副本。

```markdown
# Validation Record

## Outcome and Actual Change

## Acceptance Criteria Evidence

## Tests / Commands / Results

## Review Findings and Closure

## Affected Risk Qualities

## Remaining Risks / Risk Acceptance

## Release / Next Action
```

## Appendix C — Supplement Derivation Rules

後續 supplements 與 adoption navigation 必須直接由本 Playbook 產生：

- `README.md`：依角色導向正確 artifact 與 SSOT；Engineer 先讀 `04` 與本 Playbook，routing ambiguity 才查 `05`。
- `guides/04_Framework_Overview.md`：呈現 Golden Flow + Six Golden Questions 的單一 Engineer mental model。
- `guides/05_Decision_Tree.md`：開頭提供 compact router，再依 Six Golden Questions 導向 required capability、Golden default skill、artifact/gate。
- `training/06_Training_Presentation.pptx`：用真實 scenarios 教會 Engineer 如何開始。
- `reference/Golden_Skill_Registry.md`：管理 skill source、environment、installation、invocation、status 與 fallback。

Supplements 不新增新方法；若 supplements 暴露缺口，先修正 Framework 或 Golden Playbook，再重新衍生。

Framework Overview、Decision Tree 與 Training Presentation 必須共同呈現：

- `P3 → P2 → P1 → P0 PBI/User Story → Execution Layer`，且 Task 不列為 Work Level。
- Plan stage 的 `P1 → P0 to-tickets` 與 `P0 → tasks JIT writing-plans` 分工。
- P0 types、`Blocked by`、execution frontier，以及 Spike 的 evidence/decision outcome。
- OpenSpec Change 是 P1/P0 scope-dependent durable container；`/opsx:explore` 仍為 E0/no-stakes。
- System Design 仍在 Design stage，保留三個 Human Gates，不新增 universal gate。
- Tracker 只做 reference mapping；GitLab Milestone/Iteration 不進入 hierarchy。
- Golden Stages 是可攜式 decision states，不是部門統一 SDLC phases；Team workflow 與 templates 由 Team 擁有。
- Golden Flow + Six Golden Questions 是唯一 Engineer mental model；七段 responsibility coverage 不進入 Engineer-facing supplements。
- `Understand → Challenge → Execute → Evidence` 是每個 Stage 的 AI 基本功，不呈現為第二套 lifecycle。
- 首先問 existing work location 與最大未知/風險，再選 required capability、Golden default skill、artifact placement 與 gate。
- 新手直接採 Golden defaults；Team equivalent 必須完成 capability、input/output、stop condition、gate 與 evidence mapping。
- 既有十個以上 pilot cases 是 evidence base；選 3–5 canonical cases，其餘進 Case Library。

Decision Tree 的 opening router 同時擔任日常 quick reference；不另行維護重複的 `07` content SSOT。若需要 PDF／PNG handout，應由相同 source 產生。

## Appendix D — Change Log

| Version | Change |
|---|---|
| v1.5 | Adoption navigation correction：新增 Root README role paths 與 Golden Skill Registry；Engineer 先使用 Overview + 本 Playbook，routing ambiguity 才查 Decision Tree。Decision Tree opening router 同時擔任 quick reference，不再建立獨立 `07` content SSOT。 |
| v1.4 | Engineer mental-model correction：Golden Flow + Six Golden Questions 成為唯一 Engineer workflow；AI Work Loop 改為每個 Stage 的 AI 基本功。移除七段 formal lifecycle mapping，Skill policy 改為 required discipline + Golden default + approved equivalent mapping，避免只會 vibe coding 的 Engineer 在沒有方法下自行選擇。 |
| v1.3 | SDLC integration correction：Golden Stages 保留為穩定的 portable engineering decision states，不綁定單一 Team SDLC。加入 existing work location router、每個 Stage 的 typical touchpoints／artifact location／decision owner／process trigger、artifact placement、Team-owned workflow/templates、Agile/Sprint DoR/DoD、E3 existing authorization 與既有 pilot consolidation。 |
| v1.2 | Semantic correction：P0 改為 PBI/User Story vertical slice；Task 移至 Execution Layer；OpenSpec Change 改為 P1/P0 scope-dependent container；加入 `to-tickets` P1 → P0、per-P0 JIT `writing-plans`、blocker frontier、wide-refactor pattern 與 Azure DevOps/GitLab reference mapping。Golden Flow、三個 Human Gates 與 System Design trigger 不變。 |
