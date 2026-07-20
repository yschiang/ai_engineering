# Department Golden Engineering Playbook

> Version: v1.12 Baseline
> Status: Baseline  
> Purpose: Engineer-facing execution guide for AI-Native Software Engineering  
> Governing Framework: `02_Framework.md` v1.14
> Audience: Engineer, Senior Engineer, Tech Lead, Architect, Engineering Manager

---

## Executive Statement

這份 Playbook 是部門級的 **Golden Reference**。它不是另一份治理文件或平行 SDLC，而是工程師在既有 ticket、design、PR、test、release 與 incident activities 中可以直接使用的入口。

工程師從 §1 的 Six Golden Questions 開始：先確認工作 context、定位 Current Golden Stage 與 Next Move，再進入該 Stage 選 capability、skill、output 與 gate。OpenSpec、Superpowers、`to-tickets`、`writing-plans` 都是 Stage 內側的執行選擇，不是進場前必須先選的 framework route。

Golden Flow 是 Engineer 唯一需要使用的 workflow：

```text
Research → Design → Plan → Implement → Validate
```

Golden Stages 是可攜式 engineering decision states，不是所有 Team 必須採用的固定 SDLC phases。Team 可以把一個 activity mapping 到多個 Golden Stages，也可以讓一個 Golden Stage 跨活動或 Sprint。

在每個 Golden Stage，都使用同一組 **AI 基本功**：先 `Understand`、再 `Challenge`，接著 `Execute` 並留下 `Evidence`。它是每個 Stage 的工作紀律，不是第二套 lifecycle。

**核心規則：在大家原本就會查看的 ticket、PR、document 或 record 裡處理工作，補齊 minimum information 與 gate decision；不要另外建立沒人維護的平行文件，也不要一次啟動所有 skills。**

---

## 1. Engineer Start Here — Six Golden Questions

進入新的 work item 時，用 Team 已有資訊回答一次 Six Golden Questions；不要先選工具或建立新表單。執行中通常只更新 Current Stage 與 Next Move；scope、architecture、risk 或 AI authority 改變時才完整重判。

| Six Golden Questions | 要確認什麼 | 用途 |
|---|---|---|
| **1. 工作記在哪裡？** | 大家共同查看的 ticket、PR、design、test、release 或 incident record | 沿用既有 SSOT，避免平行文件 |
| **2. Work Level？** | P3 Product/Program、P2 Epic、P1 Feature、P0 PBI/User Story | 決定 outcome ownership 與 decomposition depth |
| **3. Archetype？** | Greenfield、Modernization/Migration、Standard Delivery | 決定 Research／Design 的起始 evidence |
| **4. Current Golden Stage？** | Research、Design、Plan、Implement、Validate | 定位目前最大的未知或風險 |
| **5. Control Profile？** | System Criticality × Change Risk × AI Execution Mode | 決定 rigor、Human control 與 evidence depth |
| **6. Next Move？** | Required capability、minimum output／evidence、decision owner | 只選目前 Stage 的下一個動作 |

### 1.1 Locate the Current Golden Stage

| 第一個還不能回答的問題 | Current Stage | 先做到什麼 |
|---|---|---|
| 系統、問題、current behavior、scope 或 root cause 是什麼？ | **Research** | 以 evidence 建立可信的 understanding，通過 Understanding Gate |
| Target behavior、boundary、trade-off 或 failure mode 是否合理？ | **Design** | 形成並 challenge selected design，通過 Change Gate |
| 如何形成可交付 outcomes 與可執行 steps？ | **Plan** | 完成必要的 delivery decomposition／implementation breakdown |
| Approved P0／Change 如何安全、小步完成？ | **Implement** | 依唯一 task ledger 做 bounded、TDD-driven change |
| 有什麼 fresh evidence 能支持完成或 release handoff？ | **Validate** | 關閉 review findings，以 evidence 進入 Evidence Gate |

### 1.2 Choose Capabilities Inside the Current Stage

Current Stage 已定位後，才選 supporting capability。**是否採用 OpenSpec，只是 Stage 內的 artifact／execution 選擇，不是 Engineer 的起始心智模型。**

| Current Stage | Stage 內才判斷的選擇 |
|---|---|
| **Research** | 依第一個未知選 `system-research`、`codebase-research`、`grill-me`、`/opsx:explore` 或 `systematic-debugging`；不要全部串接 |
| **Design** | 需要可跨 session／人／AI 延續的 durable agreement 時使用 OpenSpec proposal／specs／design；否則使用既有 ticket／design SSOT 與 Superpowers／Team equivalent |
| **Plan** | 先分清 delivery decomposition 與 implementation breakdown；規則見 §4.3 |
| **Implement** | 從既有唯一 task ledger 進場；OpenSpec 使用 `/opsx:apply`，其他 work 使用 approved plan／inline steps；實作套用 TDD、debugging 與 targeted checks |
| **Validate** | 使用 code review、fresh verification；OpenSpec 按 risk 加 `/opsx:verify`、sync、archive |

Plan Stage 的兩種拆解不可混為同一條工具鏈：

```text
Delivery decomposition
Approved P1
→ 多個獨立、可驗證 outcomes：to-tickets / Team equivalent → P0 + Blocked by
→ 一個 bounded outcome：直接視為一個 P0

Implementation breakdown
→ 已採用 OpenSpec：tasks.md 是唯一 ledger；在原檔按需展開 sub-tasks
→ 未採用 OpenSpec：simple P0 用 inline plan；multi-step/high-risk/complex P0 才用 writing-plans
```

`to-tickets` 拆的是可獨立交付的 P0 outcomes；OpenSpec `tasks.md`／`writing-plans` 拆的是 implementation steps。OpenSpec task 不會因為被列在 `tasks.md` 就自動成為 P0。

### 1.3 Confirm Triggered Context — Reuse Existing Records

先確認工作記在哪裡、Work Level、Archetype、Current Stage、Control Profile 與 Next Move。「工作記在哪裡」可以是 backlog/ticket、design/RFC、branch/PR、pipeline/test、release/change record、dashboard/incident review，或 Team 平常共同查看的其他地方。

- 優先把 artifact/evidence 寫回既有 system of record。
- 一個 existing activity 可以承載多個 Golden Stages；不要硬把 Team workflow 改成五個 phases。
- 若沒有現成位置，才依 risk、handoff 與 longevity 建立 durable artifact。

| Stage | 如果你現在還不能回答… | Golden Defaults |
|---|---|---|
| Research | 系統/問題現在如何運作？有哪些 options？真正 scope 是什麼？ | manual `system-research` / `codebase-research`；按未知加 `grill-me` / `/opsx:explore` |
| Design | 是否需要 System Design？要改成什麼、為什麼選這個方案？ | System Design when triggered；`superpowers:brainstorming`／Team design SSOT；需要 durable agreement 時用 OpenSpec proposal/specs/design；按需 `grill-with-docs` |
| Plan | P1 是否包含多個 P0？目前 P0 是否需要更詳細的 execution tasks？ | 多個 P0 才用 `to-tickets`；已採用 OpenSpec 就用同一份 `tasks.md`；未採用時才按需用 inline plan／`superpowers:writing-plans` |
| Implement | 如何按計畫小步實作並持續驗證？ | `superpowers:test-driven-development` + execution skill；OpenSpec change 以 `/opsx:apply` 進場 |
| Validate | 有什麼 fresh evidence 證明完成？ | `requesting-code-review` → `receiving-code-review` → `verification-before-completion` |

### 1.4 Detailed Capability Selector — Use Only for a Specific Unknown

| 第一個還沒搞清楚的問題 | 先用什麼 | 做到什麼就停 | 結果放哪裡／下一步 |
|---|---|---|---|
| Domain/system 全貌不清楚 | manual `system-research` | Boundary、flow、critical concepts 與 unknowns 可被解釋 | Research Brief／existing knowledge SSOT |
| Existing code 的真實 behavior/change boundary 不清楚 | manual `codebase-research` | Entry points、flow、existing pattern 與 change boundary 有 repository evidence | Research Brief／work item evidence |
| 重要規則、constraint 或 decision 在 Owner/operator 腦中 | `grill-me` | 關鍵決定、假設、examples 與 open questions 已經說清楚 | `grill-me` 本身不保存正式文件；需要交接時寫回 work item／design／OpenSpec |
| 有 problem，但是否要 change、scope 或 options 尚未清楚 | `/opsx:explore` | 可以停止，或已清楚到能提出 change | E0 conversation only；不寫 artifact/code；繼續時交 `/opsx:propose` 或 `/opsx:new` |
| Bug/incident root cause 未證明 | `superpowers:systematic-debugging` | Reproduction 與 root cause 有 evidence | Incident／Bug context；再進 targeted design/fix |
| P3/P2，或 P1 符合 System Design trigger | System Design | Boundary、architecture、NFR、failure/recovery 與 decomposition 可 review | Product/Architecture SSOT；P1 bounded delta 可放 OpenSpec `design.md` |
| 已決定要新增／改變 behavior，但 target behavior、approach 或 trade-offs 未 approved | `superpowers:brainstorming` 或 Team equivalent | Selected design 已寫下並由 Human Owner approval | Selected design SSOT |
| 已有 design/spec，需要找 contradiction、missing case 或 weak decision | `grill-with-docs` | Material findings closed | 更新原 artifact，不建立平行 review document |
| Direction 已清楚，而且下一個 session、AI 或 Engineer 必須接著同一份 why／what／how／tasks 工作 | `/opsx:propose`；複雜 change 用 `/opsx:new` + `/opsx:continue` | Proposal、specs、design、tasks 已足以 review 和接續執行 | OpenSpec Change；套用相同 design quality contract，不另跑會產生第二份文件的 skill |
| Approved P1 包含多個獨立 outcome，尚未切成 sprint-ready slices | `to-tickets` | P0 tracer bullets 可獨立驗證，且 blockers/frontier 清楚 | Existing tracker；由 P1 OpenSpec `tasks.md` reference when used |
| 未採用 OpenSpec：單一 P0 即將執行，且 multi-step/high-risk/complex | `superpowers:writing-plans` | Exact files/interfaces/tests/commands 可直接執行 | Upstream plan output，或 Team 已核准的等價 plan SSOT |
| 已採用 OpenSpec：執行到的 task 顆粒過粗 | 在 `/opsx:apply` 當下直接於 `tasks.md` 展開巢狀子項 | 每個子項列 exact files、failing test、green criterion | Engineer 快速確認後繼續；不呼叫 `writing-plans`、不另開文件 |
| P0 與必要 plan ready | `superpowers:test-driven-development` + execution skill；有 OpenSpec 時由 `/opsx:apply` 進場 | 每個 task 完成 Red-Green-Refactor 與 targeted check | Code/tests/task state |
| Implementation ready，需要宣稱完成 | `requesting-code-review`；收到 findings 後用 `receiving-code-review` 技術驗證，再執行 `verification-before-completion`；OpenSpec 按 risk 加 `/opsx:verify` | Findings closed，completion claims 有 fresh evidence | PR／Validation Record；再 sync/archive when used |

未知關閉後，重新確認 Current Stage 與 Next Move；不要把 discovery capabilities 串成固定流程。Team 可以選 approved equivalent，但不能降低 architecture/risk trigger、TDD/test/review、Human Gate 或 evidence quality。

### 1.5 During Execution — Re-evaluate Only Changed Context

Work Level、Archetype 與 Control Profile 已在 initial routing 判定。持續執行時沿用原判斷；出現下列變化才重新判定，不必在每個 task 重填六題。

| Context change | 重新判定 | 用途 |
|---|---|---|
| 需要拆 Product／Epic／Feature／P0，或決定 artifact/review depth | **Work Level** | Delivery decomposition 與 handoff；詳見 §2.5、§5–9 |
| Greenfield、migration/modernization 的 research/design focus 明顯不同 | **Archetype** | 選擇 starting evidence 與 validation focus；一般 bounded delivery 不必重複標記 Standard |
| 高 criticality、L2–L3 change，或 AI 將影響 shared/external/production state | **Control Profile** | 決定 rigor、evidence 與 E3 authorization；詳見 Framework §5 |

**Initial route 要完整；execution loop 要聚焦。不要每一步重新分類，也不要一次啟動所有 skills。**

Research 的 `system-research` 與 `codebase-research` 是不需安裝即可執行的 manual capability defaults；Candidate skill 只有在 Registry 標示 approved 後才可取代。System Design 等工程活動仍由 Engineer／Architect 執行；其他 installable skill entries 依 Registry 的 approved mapping 使用。Team 採用 equivalent 時，必須接受相同 required inputs、產出相同 minimum artifact、遵守相同 stop condition、通過相同 gate，並保留相同 evidence quality。

---

## 2. Golden Delivery Flow

### 2.1 Golden Flow — The Only Engineer Workflow

| Golden Stage | Covered Capabilities | Engineer 的核心問題 |
|---|---|---|
| Research | Understand + Explore + Define | 現況、問題、boundary、options、unknowns 與 scope 是什麼？ |
| Design | System Design when triggered + Feature/Detailed Design + Challenge | Boundary、target behavior、architecture、trade-offs、failure behavior 是否站得住腳？ |
| Plan | Conditional delivery decomposition + JIT implementation planning | 這個 P1 是否需要多個 P0？目前這個 P0 需要哪些 execution tasks？ |
| Implement | TDD + bounded execution | 如何依 plan 以 TDD/controlled change 完成？ |
| Validate | Verify + release handoff | Requirement、risk、quality 是否有 fresh evidence？ |
| Release / Operate | Existing SDLC overlay | 如何安全 release、observe、rollback/recover、learn？ |

Release 與 Operate 不從 Golden Flow 消失；它們由既有 release/change/SRE process 承接，並使用 Validate stage 產生的 evidence。

這張表只展開 Golden Stage 內部涵蓋的 capabilities，不定義第二套 lifecycle。Team 的 Intake、Refinement、Sprint、PR、Release 或 Incident flow 可以合併、改名、重排；只要保留 Golden Stage 的工程問題、minimum contract、decision owner 與 risk-based evidence。

Shared／external／production action 必須經既有 Release／Change Management 與 authorized owner。AI 可以準備 plan、validation、rollback 與 evidence，但不能成為 production approver；irreversible migration、destructive operation 與 production mutation 一律需要 explicit authorization。Canonical E3 sequence 見 [Framework §4.6](02_Framework.md#46-release-change-management-and-e3-integration)，本 Playbook 不維護第二份流程圖。

### 2.2 OpenSpec and Superpowers — Stage-Internal Roles

| Stage 內的情況 | Spec／plan owner | Implementation rule |
|---|---|---|
| **沒有採用 OpenSpec** | Existing ticket／design／plan／PR chain | Superpowers／Team equivalent 提供 design、planning、TDD、review、verification disciplines |
| **已採用 OpenSpec Change** | OpenSpec proposal／specs／design／tasks | `/opsx:apply` selects and tracks the task；Superpowers TDD/review disciplines control how code is changed |

> **OpenSpec 決定做什麼並保存 agreement；Superpowers TDD 決定每個 task 怎麼安全實作。**

這個選擇只在 Design／Plan／Implement／Validate 的 Stage 內協助決定 artifact owner 與 execution method，不取代 Six Golden Questions 或 Golden Flow。只要遵守兩條規則：同一 change 只有一份 spec/design/plan/task ledger，且 automation 只提供 evidence，Change Gate／Evidence Gate 仍由 Human Owner 決定。Team 可以自訂 local shorthand，但 Framework 不要求 Engineer 先選 artifact profile。

若 OpenSpec `tasks.md` 顆粒過粗，就依 §4.5 在 `/opsx:apply` 當下直接展開子項；不要另建 plan。

### 2.3 Spec-to-TDD Handoff Contract

| Moment | Engineer / Agent action | Record updated |
|---|---|---|
| Spec ready | Human review OpenSpec proposal/specs/design/tasks；未通過就不 implement | OpenSpec Change + Change Gate record |
| Start implementation | 建立 isolated worktree；以 `/opsx:apply` 開啟 selected Change | Existing OpenSpec task ledger |
| Execute one task | 使用 `superpowers:test-driven-development`：RED → GREEN → REFACTOR → targeted verification | Code、tests、同一個 OpenSpec task state |
| Unexpected failure | 暫停猜測式修補，使用 `superpowers:systematic-debugging` 證明 root cause，再回 TDD loop | Reproduction/root-cause evidence |
| Review | `requesting-code-review` → 以 `receiving-code-review` 驗證 findings → 修正後重跑 tests | PR findings + closure evidence |
| Verify whole change | `verification-before-completion` + `/opsx:verify`；確認 acceptance 與 affected risks | PR／Validation Record |
| Close | Human Evidence Gate；通過後 `/opsx:sync` → `/opsx:archive` | Gate decision + durable specs/history |

在 `/opsx:apply` session 中可使用以下 execution contract；它只約束已選定的 Implement work，不是 initial routing：

```text
Apply the selected OpenSpec Change. Treat its specs, design and tasks as the only implementation SSOT.
For each unchecked task, use test-driven development: observe the correct failing test, make the minimum
implementation pass, refactor only while green, and run targeted verification. Do not mark a task complete
without fresh evidence. If implementation requires a spec, design or scope change, stop and use /opsx:update.
Do not create another design, plan or task ledger.
```

如果 implementation 發現 spec、design 或 scope 要改，先停下來更新 OpenSpec artifacts 並重新取得 Change Gate decision；不要讓 code 默默取代 agreement。

P3/P2 的 product/target architecture 仍放在 Product/Architecture SSOT；OpenSpec 只承載 bounded P1/P0 change。詳細 tool provenance、bridge candidate 與 edge cases 留在 Skill Registry，不放進 Engineer start path。

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
- P1 決定 bounded outcome、feature behavior；只有包含多個獨立 outcome 時，才用 `to-tickets` 切成 P0 vertical slices。
- P0 是可進 Sprint、可獨立驗證的 delivery slice；即將執行時才按需產生 implementation plan。
- Execution Layer 執行最小 test/change/review loop，不升格為 Delivery Level。

每個 level 都有自己的 Research → Design → Plan → Implement → Validate，但深度不同。

---

## 3. Department Skill Catalog

### 3.1 Skill Family A — Understand and Research

| Skill | Use When | Primary Output | Stop Condition |
|---|---|---|---|
| **`system-research`** | Domain/system unfamiliar、資料跨多來源、需要建立全貌 | Knowledge map、glossary、system/domain model、unknowns | 能描述 boundary、flow、critical concepts 與 unknowns |
| **`codebase-research`** | 既有 repository、需要以 code/test/history 證明 behavior | Code map、entry points、call/data flow、patterns、evidence links | Change boundary 與 existing pattern 已定位 |
| **`grill-me`** | 需求/規則主要在 Owner 或 operator 腦中 | Structured Q&A、decisions、assumptions、examples、open questions | Material tacit knowledge 已外顯並確認 |
| **`grill-with-docs`** | 已有 PRD/design/runbook，需要嚴格挑戰 | Evidence-based findings、missing cases、decision questions | Blocker ambiguity/contradiction 已關閉 |
| **`superpowers:systematic-debugging`** | Bug、incident、test failure、unexpected runtime behavior | Facts、hypotheses、falsification result、root cause | Root cause 有 reproduction/evidence，不是猜測 |

`system-research` 與 `codebase-research` 在本版是 **capability aliases**：Engineer 直接使用 Registry 內的 read-only prompt/manual contract，不依賴尚未核准的第三方 skill。`understand-anything` 目前只是 `system-research` 的 candidate equivalent。

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

這條 artifact chain 不代表 hierarchy。OpenSpec Change 必須宣告 scope：coherent P1 Feature，或 why／what／how／tasks 需要交接或長期維護的 P0 PBI；不得把 `Change` 當成 P0 同義詞。

### 3.3 Choosing the Research / Explore Tool

| Need | Start With | Why |
|---|---|---|
| 建立跨文件、domain、system 的整體理解 | `system-research` | 產生 structured knowledge model 與 unknowns |
| 找出既有 code 的真實 behavior、entry point、dependency | `codebase-research` | 以 repository evidence 定位 change boundary |
| 把 Owner/operator 腦中的規則問出來 | `grill-me` | 外顯 tacit knowledge、examples 與 decisions |
| 有問題但還不確定要不要/怎麼形成 change | `/opsx:explore` | 在 no-stakes、no-artifact 狀態比較 options 與 scope |
| 已有文件，需要找 contradiction、missing case、weak decision | `grill-with-docs` | 對 artifact 做 evidence-based challenge |

這些能力可以在不同時點接續使用，但不要一次全部啟動。先找出第一個還沒搞清楚的問題，只選能回答它的 capability；得到結果後再重新判斷。

### 3.4 Design and Plan Activities / Skills

| Activity / Skill | Use When | Primary Output | Gate |
|---|---|---|---|
| **System Design** | P3/P2；或 P1 涉及跨 boundary/contract/data、重大 NFR、novel architecture、L2–L3 | System Design Pack、ADRs、Epic/Feature decomposition | System Design Review under Change Gate |
| **`improve-codebase-architecture`** | 已有 as-is evidence，且明確要評估 architecture improvement／refactor opportunities | Architecture friction candidates、before/after、recommendation strength、top recommendation | Human selects candidate；再交給 System Design 或 Feature/Detailed Design，不直接 implementation |
| **`superpowers:brainstorming`** | 新 functionality、behavior change、architecture option、需求仍需釐清 | Approved design/spec、options/trade-offs | Design owner approves direction |
| **`grill-with-docs`** | Design/spec 已形成，需要 adversarial review | Findings + minimal corrections | Material risks/ambiguities closed |
| **`to-tickets`** | Approved P1 包含多個獨立 outcome，需要切成 Sprint-ready delivery slices | P0 tracer-bullet tickets、acceptance、`Blocked by`、execution frontier | 每張 P0 narrow but complete、可獨立驗證；單一 bounded P1 不使用 |
| **`superpowers:writing-plans`** | 未採用 OpenSpec 的單一 P0 即將執行，且 multi-step、high-risk 或 complex | JIT executable plan：exact files/interfaces、steps、tests、commands、evidence | Plan 可由沒有背景的 Engineer 執行；無 unresolved design decision |

System Design 是由 Engineer／Architect 負責的一般工程活動，不是 skill、command 或固定 tool pipeline，也不依賴本表中的任何 skill。`brainstorming`、`grill-with-docs` 與其他 AI skills 只在有對應未知或 review 需要時選用。

Planning responsibility：

```text
Approved P1
→ 若包含多個獨立 outcome：to-tickets → 多個 P0 + blockers
→ 若本身是一個 bounded slice：直接視為一個 P0
→ 每個 P0：若已採用 OpenSpec，使用同一份 tasks.md
             否則使用 inline plan，或按需 writing-plans
→ Execution Layer tasks / plan steps / commits
→ TDD / Implement / Verify
```

- 所有 P0 明確寫 `Blocked by`；沒有 blocker 的項目構成 **execution frontier**。
- Wide refactor 使用 `expand → migrate batches → contract`，每批為可驗證 P0；不要建立一張跨越全程的大 task。
- 不先替整個 Epic 建立巨大 implementation plan。
- 未採用 OpenSpec 的簡單、低風險、單一步驟 P0 可跳過完整 `writing-plans`，但仍保留 acceptance、test direction 與 evidence。

### 3.5 Skill Family D — Implement

| Skill | Use When | Primary Output | Gate |
|---|---|---|---|
| **`superpowers:using-git-worktrees`** | 開始 feature/plan execution，需要隔離 workspace | Isolated worktree + baseline state | Workspace、安全與 baseline tests ready |
| **`superpowers:test-driven-development`** | Feature、bugfix、refactor、behavior change | Red-Green-Refactor evidence + production code | 先看到正確 failure，再看到 pass |
| **`superpowers:executing-plans`** | 已有 approved non-OpenSpec plan，需要在另一 session 分批執行 | Completed plan batches + review checkpoints | 每批 plan items 與 evidence completed |
| **`superpowers:subagent-driven-development`** | Approved plan tasks mostly independent，可在同一 session 分工 | Per-task implementation + spec/quality review | 每 task 通過 review，最後 whole-change review；不得建立第二份 ledger |
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
2. **Golden default execution**：每個 Golden Stage 提供可直接採用的 manual capability contract 或 approved skill/path，作為新手與只會 vibe coding Engineer 的起始標準。
3. **Equivalent mapping allowed**：成熟 Team 可依 approved tool、技術棧與 workflow 使用 equivalent skill，但須在 Skill Registry 證明相同 required input、output、stop condition、gate 與 evidence quality。

因此 `Golden default` 不是唯一工具，但也不是可忽略的隨意建議；未完成 equivalent mapping 時，預設採用 Department Golden skill。

Golden default 的 source、environment、installation、invocation、verification status 與 fallback 由 [`reference/Golden_Skill_Registry.md`](reference/Golden_Skill_Registry.md) 管理。Playbook 擁有 capability 與 execution contract；Registry 擁有 implementation provenance，不在兩處重複維護安裝資訊。

System Design 不屬於 Skill Registry，也沒有 installation 或 invocation。Engineer／Architect 依既有工程方法完成設計；需要 AI 輔助時，再依主要未知選用 Research、option shaping 或 document review skills。Accountable Architect／Tech Lead 仍依 trigger 完成 System Design Review。

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

`to-tickets` 是 department delivery-decomposition capability；reference implementation 來自 Matt Pocock `to-tickets`。它的條件式 ownership 是「需要多個獨立 P0 的 P1 → P0」，不是每個 P1 的固定步驟；單一 bounded P1 直接走 P0 route。

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
| Golden default capabilities | 依主要未知選 manual `system-research`、manual `codebase-research`、`grill-me` 或 `/opsx:explore`；bug/incident 加 `systematic-debugging` |
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

System Design trigger 的 canonical rule 維護於 [Framework §8.3](02_Framework.md#83-system-design-scope-and-trigger)。Operational guardrail：P3/P2 required、P1 risk-triggered、P0 normally skip；詳細 trigger 不在本 Playbook 複製。

| Item | Golden Standard |
|---|---|
| Inputs | Approved Research Brief、current/as-is model、constraints、existing architecture/rules |
| Optional AI aids | 無必要 skill dependency；依主要未知選用 Research skills、`superpowers:brainstorming` 或 `grill-with-docs` |
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

System Design Pack 是內容契約，不是指定檔名或 template；可由既有 System Design Document (SDD)、RFC、architecture document、ADRs，或 P1 OpenSpec `design.md` 承載，避免建立重複文件。

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

**Goal**：分開回答兩個問題：approved Feature 是否需要多個可交付的 P0 outcomes，以及目前 Change／P0 需要哪些安全、可驗證的 implementation tasks。

| Planning Depth | Input | Golden Default Skill | Minimum Artifact | Gate |
|---|---|---|---|---|
| **Delivery decomposition** | P1 Feature + Approved Design，且包含多個獨立 outcome | `to-tickets` | P0 PBI/Story tracer bullets + acceptance + `Blocked by` | 每張 P0 narrow but complete、Sprint-ready、可獨立驗證；frontier 可開始；單一 bounded P1 直接進 P0 route |
| **Implementation breakdown — no OpenSpec** | 單一即將執行的 P0 + repository context | Inline plan；需要時 `superpowers:writing-plans` | Exact files/interfaces/tests/commands 的 executable plan | 每個 task 可獨立理解、test、review；無 unresolved design decision |
| **Implementation breakdown — OpenSpec in use** | Approved OpenSpec Change | OpenSpec `tasks.md` only | Single task ledger；粗 task 在 `/opsx:apply` 時就地展開 | Engineer 快速 checkpoint；design change 另走 `/opsx:update` |

Typical existing integration：delivery decomposition 通常發生於 backlog refinement／iteration planning，P0 set 與 `Blocked by` 留在 tracker。未採用 OpenSpec 時，implementation plan 留在單一 P0 或 Superpowers plan；已採用時只使用 OpenSpec `tasks.md`。Product/Engineering Owner 對 P0 outcome/dependency accountable，Change Owner 對 executable tasks accountable。正常情況不新增 planning ceremony；只有 dependency、risk 或 design ambiguity 需要既有 owner/reviewer 介入。

P0 tracker items 與 OpenSpec tasks 可以同時存在，因為它們代表不同語意層級：tracker 保存 independently deliverable outcome、acceptance 與 `Blocked by`；OpenSpec `tasks.md` 保存 implementation breakdown。P1-scoped Change 如涵蓋多個 P0，`tasks.md` reference P0 IDs，不複製 acceptance 或在兩處維護相同 execution tasks。

Delivery decomposition rules：

- Slice by end-to-end behavior，不按 layer/component 產生「先 DB、再 API、再 UI」的水平 tickets。
- 每張 P0 明確列出 `Blocked by`；沒有 blocker 的 P0 是 execution frontier。
- Wide refactor 使用 `expand → migrate batches → contract`；migration batches 各自可驗證。
- P3/P2 先拆到 P1；不要替整個 Epic 建立一份 implementation plan。
- `to-tickets` 只在一個 P1 需要多個獨立 P0 時使用；單一 bounded P1 不需要先建立 tickets。

未採用 OpenSpec 時，implementation planning 採 **just-in-time**。簡單、低風險、單一步驟 P0 可用 inline plan，跳過完整 `writing-plans`。需要完整 plan 時，每個 task 至少包含：

- Goal and scope。
- Exact files / interfaces。
- Expected behavior。
- Failing test or verification first。
- Minimal implementation steps and commands。
- Completion evidence。
- Dependency on previous/next tasks。

已採用 OpenSpec 時不呼叫 `writing-plans`。OpenSpec `tasks.md` 本身具有 implementation breakdown 能力，並是唯一 task ledger；顆粒過粗時依 §4.5 在原檔就地展開。

### 4.5 Implement

**Goal**：依 plan 小步完成 change，不擴張 scope，持續產生 evidence。

| Item | Golden Standard |
|---|---|
| Inputs | Approved inline／written plan，或 approved OpenSpec `tasks.md`；isolated workspace、baseline tests |
| Golden default skills | 未採用 OpenSpec：`using-git-worktrees` → `test-driven-development` → selected Superpowers execution skill；已採用 OpenSpec：isolated workspace → `/opsx:apply` 讀取唯一的 `tasks.md`，並套用 TDD/debugging discipline；不使用 `writing-plans` 或第二個 ledger |
| Activities | Red-Green-Refactor、small commits、per-task self-review、unexpected failure root-cause analysis |
| Minimum artifact | Code/config/migration + tests + task state；使用 OpenSpec 時只更新同一份 `tasks.md` |
| Gate | 每個 task 通過 plan compliance 與 targeted verification |
| Typical existing activities | Development、branch、migration/configuration preparation、pairing |
| Where it normally lives | P0 work item／Task child item、branch、commits、code/config、test output；OpenSpec change 只在已採用時更新 |
| Decision owner | Change Owner；reviewer 對 accepted diff 仍負責 |
| Additional process required? | Normally no；沿用 existing development controls，L2/L3 依 risk 增加 review/segmentation |

Execution choice：

| Situation | Use |
|---|---|
| Small feature/task、單一 Engineer/session | Direct TDD execution |
| Approved multi-task plan、tasks mostly independent、同一 session | `subagent-driven-development` |
| Approved non-OpenSpec plan 交給另一 session 分批執行 | `executing-plans` |
| OpenSpec Change with `tasks.md` | `/opsx:apply`；subagent 如被使用也只能協助當前 task，不得擁有另一份 plan/ledger |
| Failure/root cause unknown | 暫停 random patch，改用 `systematic-debugging` |

#### OpenSpec Change — `tasks.md` Single Ledger + JIT Breakdown

這兩條規則一起使用：因為 `tasks.md` 是唯一一本帳，粗 task 的細節必須直接長在同一份 `tasks.md`，不能另開 plan。

**1. `tasks.md` 是唯一 task ledger**

- `/opsx:apply` 只從 `tasks.md` 取 task、執行並更新 checkbox。
- 任何 session、AI 或 Engineer 接手時，都以 `tasks.md` 判斷目前進度與下一個 task。
- 不建立第二份 plan 或 ledger。OpenSpec Change **不得使用 `superpowers:writing-plans`**；該 skill 會另外產生 `docs/superpowers/plans/` 文件，造成 dual SSOT。

**2. 粗 task 在執行當下做 JIT breakdown**

當 `/opsx:apply` 走到一個包含多個獨立實作單位的 task 時：

1. 先不要修改 code。
2. 直接編輯同一份 `tasks.md`，將該 task 展開為 `1.2.1`、`1.2.2` 等巢狀子項。
3. 每個子項寫明 exact file paths、先寫的 failing test，以及什麼 test 轉綠才算完成。
4. Engineer 快速確認展開結果後繼續 `/opsx:apply`。這是 execution checkpoint，不是新的 Human Gate。

這是 `/opsx:apply` 期間直接更新 artifact 的正常行為，不需要額外 skill。

Before：

```markdown
- [ ] 1.2 Implement idempotent payment capture
```

After：

```markdown
- [ ] 1.2 Implement idempotent payment capture
  - [ ] 1.2.1 Update `tests/payments/capture-idempotency.test.ts` and
        `src/payments/capture-service.ts`: first add a failing same-key retry test;
        done when two identical requests return one payment and call the gateway once.
  - [ ] 1.2.2 Update `tests/payments/capture-concurrency.test.ts` and
        `src/payments/idempotency-store.ts`: first add a failing concurrent-duplicate test;
        done when concurrent requests create one capture record and both receive the same result.
  - [ ] 1.2.3 Update `tests/payments/capture-timeout.test.ts` and
        `src/payments/capture-controller.ts`: first add a failing retry-after-timeout test;
        done when the retry reuses the completed capture without a second gateway charge.
```

邊界判斷：

> **只長出子項是 JIT；改變做法是 design change。**

如果只是補 files、tests、順序與完成判準，直接更新 `tasks.md`。如果新做法與 `design.md` 不一致，停止 implementation，使用 `/opsx:update` 更新 design，並依 scope/risk 判斷是否重新通過 Change Gate。

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

Stage ownership 在 Validate，但 invocation 可以提早：`requesting-code-review` 在 subagent-driven development 每個 task 後、major Feature 完成後及 merge 前使用；收到 feedback 時先以 `receiving-code-review` 對照 codebase/tests 做技術驗證。需要修改時回到 Implement 小步修正並測試，再返回 Validate；review suggestion 不是自動 approval 或 implementation instruction。

完成後再使用 `finishing-a-development-branch` 進入 merge/PR/cleanup decision；OpenSpec change 在 evidence 與 release decision ready 後執行 `/opsx:sync` 與 `/opsx:archive`。

---

## 5. P3 Playbook — Greenfield Product

### 5.1 Objective

從模糊機會建立可交付 product direction、architecture runway 與可驗證 MVP，並拆成 Epics/Features；不得直接用一份大型 prompt 產生完整 product。

### 5.2 Golden Flow

| Stage | Golden Defaults / Optional AI Aids | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | manual `system-research`、`grill-me`、`/opsx:explore` | Problem、users/workflow、domain、constraints、success metrics、unknowns、options | Product Research Brief、Domain/Workflow Map | Product/Engineering Owner confirms problem and boundary |
| Design | System Design；AI aids optional | Product/domain design → system context、boundaries、runtime/data、NFR、operating model、MVP architecture | Product/Domain Design、System Design Pack、initial ADRs | Product approval + System Design Review |
| Plan | Portfolio decomposition / roadmap planning | MVP scope、Epic map、dependency order、architecture runway、validation plan；不建立 program-level implementation plan | Product Roadmap、Epic Backlog、MVP Evidence Plan | Roadmap decomposable into P2 Epics |
| Implement | P2/P1/P0 playbooks | Build vertical slices；每個 Epic/Feature 走自己的 Golden Flow | Working increments、tests、decision/evidence ledger | Per-Epic/Feature gates |
| Validate | code review、verification、product evidence | User/business acceptance、architecture conformance、NFR、operational readiness | MVP/Product Validation Report | Product Owner + Service Owner go/no-go |

**OpenSpec scope rule**：P3 direction、product architecture 與 roadmap 使用產品/架構 SSOT；不要建立一個涵蓋整個 product 的巨型 OpenSpec change。Change container 只承載 coherent P1 Feature，或 why／what／how／tasks 需要交接或長期維護的 P0 PBI。

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

| Stage | Golden Defaults / Optional AI Aids | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | manual `system-research`、manual `codebase-research`、`grill-me`、`/opsx:explore`、`systematic-debugging` | As-is behavior、entry points、dependencies、data、operations、incidents、hidden rules、migration options | As-Is System Model、Behavior Catalog、Dependency/Data Map、Unknowns | Domain + Legacy Owner confirms model |
| Design | System Design；AI aids optional | Target System Design、seams/strangler、compatibility、migration/data strategy、failure/recovery | Target System Design Pack、Migration Strategy、Compatibility Contract、ADRs | System Design Review + Service Owner approval |
| Plan | Migration roadmap / wave decomposition | Characterization baseline、migration waves、parallel run、cutover/rollback、Epic/Feature breakdown；不建立跨 waves implementation plan | Modernization Roadmap、Wave Plans、Parity/Evidence Matrix | Each wave bounded and recoverable |
| Implement | worktree、TDD、executing/subagent-driven development | Characterization first、incremental replacement、dual-run/adapters when needed | Migrated slices、tests、reconciliation evidence | Per-wave compliance and quality review |
| Validate | review、verification-before-completion | Behavior parity/correction、performance、data reconciliation、failure/recovery、cutover rehearsal | Migration Validation Record、Cutover Readiness | Domain + Service Owner go/no-go |

**OpenSpec scope rule**：不要把多年 modernization roadmap 或整個 wave 塞進單一 change folder。Wave 由 roadmap/architecture artifacts 管理；其中 coherent P1 Feature，或 why／what／how／tasks 需要交接或長期維護的 P0 PBI，才各自使用 bounded Change container。

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

| Stage | Golden Defaults / Optional AI Aids | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | manual `system-research`、manual `codebase-research`、`grill-me` | Capability outcome、affected systems/contracts/data、dependency、NFR、unknowns | Epic Research Brief、Impact Map | Epic Owner confirms outcome/scope |
| Design | System Design；AI aids optional | End-to-end flow、System Design/architecture delta、contracts、feature boundaries、failure modes | Epic System Design Pack、Feature Map、ADRs | System Design Review by Tech Lead/Architect |
| Plan | Feature decomposition / delivery planning | Sequence Features、integration milestones、test/release strategy；不建立 Epic implementation plan | Epic Delivery Plan、Feature Backlog、Integration Evidence Plan | Features independently testable/releasable |
| Implement | P1/P0 playbooks | Execute each Feature；maintain contract/integration ledger | Feature increments、contract tests | Feature gates + periodic Epic review |
| Validate | code review、verification | End-to-end capability、contract compatibility、NFR、rollout readiness | Epic Validation Record | Epic Owner accepts capability |

**OpenSpec scope rule**：Epic Design/Feature Map 管方向；OpenSpec Change 不作為 Epic hierarchy level。每個 coherent P1 Feature，或 why／what／how／tasks 需要交接或長期維護的 P0 PBI，使用自己的 scoped change。

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

| Stage | Golden Defaults / Optional AI Aids | Key Activities | Required Artifact | Human Gate |
|---|---|---|---|---|
| Research | manual `codebase-research`；模糊時 `/opsx:explore`；必要時 `grill-me` / `system-research` | Current behavior、existing pattern、impact、acceptance、risk、options | Feature Research Brief / ticket context | Owner confirms problem and boundary |
| Design | Triggered 時進行 System Design；需要讓後續 session／AI／Engineer 沿用同一份 change context 時用 `/opsx:propose`；其他 AI aids optional | System boundary/architecture delta when triggered；target behavior、contracts/data/failure、test strategy | Triggered System Design Pack/ADR + Proposal + Specs + Design | System Design Review when triggered；Feature Design approved |
| Plan | Delivery decomposition：多個 outcome 才用 `to-tickets`，單一 bounded P1 直接作為 P0；implementation breakdown 對即將執行的 P0 採 JIT | 需要時切 P0 tracer bullets 與 `Blocked by`；每張 P0 已採 OpenSpec 時沿用 `tasks.md`，否則使用 inline steps／triggered `writing-plans` | P0 Backlog + Dependency Graph when split；每張 ready P0 只有一份 implementation ledger／plan | P0 narrow but complete、Sprint-ready；tasks bounded、可驗證，且沒有 unresolved design decision |
| Implement | 從 ready P0 的唯一 implementation ledger／plan 進場；OpenSpec 使用 `/opsx:apply`，其他 work 直接依 approved steps 執行 | 逐張 P0 Red-Green-Refactor、small commits、per-task checks | P0 increments + tests + updated ticket/task state | Per-P0 reviews pass |
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
| Research | manual `codebase-research` | Affected files/behavior、existing pattern、risk |
| Design | Short `brainstorming` when behavior changes | Selected approach + must-not-change |
| Plan | 已採用 OpenSpec：只用同一份 `tasks.md`；未採用：單一步驟用 inline plan，multi-step/high-risk/complex 才用 JIT `writing-plans` | Exact steps、files/interfaces、tests、commands |
| Implement | `test-driven-development` | Failing test → minimal change → pass |
| Validate | code review as required + `verification-before-completion` | Fresh targeted/full test evidence |

P0 不預設要求 OpenSpec。若 P0 涉及 durable behavior agreement、多人 handoff 或需長期維護的 spec，可建立 **P0-scoped** OpenSpec Change；此時 `tasks.md` 是唯一 ledger，粗 task 在 `/opsx:apply` 中就地展開。若實際 scope 改變 architecture boundary 或已不是單一 vertical slice，才重新分類為 P1/P2。純 mechanical L0/L1 P0 可直接使用 ticket + PR evidence。

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
- 若目標是評估 architecture improvement opportunities，先用 `codebase-research` 建立 as-is evidence；進入 Design 後才可按需使用 `improve-codebase-architecture`。它產生候選與 recommendation，不直接授權 code change。
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

## 10. Golden Selection Matrix

### 10.1 Responsibility Ownership Map

這張表先回答「誰對什麼負責」；下一張 Stage Matrix 才回答「哪個 skill 可能在哪個 Stage 使用」。

| Responsibility | Default Implementation | Stage Coverage | Selection Rule |
|---|---|---|---|
| Direction／roles | Existing Team workflow and owners | All stages + Release/Operate | 不新增 virtual roles 作 Department requirement |
| Spec-Driven Development | OpenSpec | Design → Plan → Implement → Validate | 需要 durable agreement/change traceability 時使用；其他 work 沿用既有 SSOT |
| Engineering discipline | Superpowers／Team equivalent | Design → Plan → Implement → Validate | 清楚的 P0/P1 可獨立採完整 workflow；mixed mode 只選不重複 artifact 的 disciplines |
| Execution orchestration | `/opsx:apply`、Superpowers execution 或 approved runner | Implement | 每個 change 一個 execution entry、一個 task ledger |
| Evidence／approval | CI、PR、tests、review、OpenSpec verify + Human Gate | Validate + Release handoff | Automation 證明；Human Owner 決定 |

### 10.2 Stage × Activity / Skill

這張 Matrix 呈現 Department Golden activities 與 skills。`Primary` 表示該情境的預設安全路徑，不代表每個 work item 都要執行所有列；initial routing 先用 Six Golden Questions 選定 column、current stage 與 control，執行中再依 Current Stage／Next Move 選下一個 activity。System Design 沒有 installation／invocation；其他 installable entries 依 Skill Registry 使用 approved mapping。

| Activity / Skill | Research | Design | Plan | Implement | Validate |
|---|:---:|:---:|:---:|:---:|:---:|
| system-research (manual default) | Primary for broad/unfamiliar context | Support |  |  |  |
| codebase-research (manual default) | Primary for existing systems | Support evidence | Support file map | Support pattern lookup | Support traceability |
| grill-me | Primary for tacit knowledge | Support decisions |  |  |  |
| `/opsx:explore` | Primary for no-stakes option/scope exploration | Handoff only |  |  |  |
| `/opsx:propose` or `new/continue/ff` | Research inputs | Primary durable agreement | Durable task/ticket references |  | Alignment reference |
| grill-with-docs | Review research | Primary design challenge | Review plan when high risk |  | Review evidence/doc consistency |
| System Design | Evidence inputs | Primary for P3/P2 and triggered P1 | Architecture/decomposition handoff | Conformance reference | Architecture conformance evidence |
| improve-codebase-architecture |  | Optional for explicit architecture improvement/refactor assessment；Human-selected candidate hands off to formal design |  |  |  |
| brainstorming | Scope/problem exploration | Primary | Handoff to `to-tickets` |  |  |
| `to-tickets` |  | Approved design input | P1 → 多個 P0 時使用 | Delivery contract | P0 acceptance rollup |
| writing-plans |  |  | 未採用 OpenSpec 時，per-P0 JIT only | Execution contract | Plan compliance check |
| systematic-debugging | Primary for incidents/bugs | Root-cause-informed design | Targeted fix plan | Failure handling | Reproduction verification |
| test-driven-development |  | Test strategy | TDD task steps | Primary | Red-Green evidence |
| executing-plans / subagent-driven-development |  |  | Read approved plan | Multi-task work；保持唯一 ledger | Completion ledger |
| `/opsx:apply` |  |  | Reads tasks | OpenSpec execution entry | Task/artifact alignment |
| requesting/receiving-code-review |  |  |  | Per-task review | Primary |
| verification-before-completion |  |  |  | Per-task claims | Mandatory before completion claim |
| `/opsx:verify` |  |  |  |  | Expanded artifact/implementation verification |
| `/opsx:sync` + `/opsx:archive` |  |  |  |  | Update durable truth and close change |
| finishing-a-development-branch |  |  |  |  | After validation |

### 10.3 Trigger Rules

最容易混淆的四個 capabilities 先用下表分流；詳細 selector 見 §1.4。

| 你現在需要的是… | 先用什麼 | 做到哪裡／不要拿它做什麼 |
|---|---|---|
| 從 Owner/operator 腦中取得並壓力測試 decisions | `grill-me` | 問到關鍵決定、假設與 examples 清楚；正式結論另存回 SSOT |
| 在尚未承諾 change 前探索 problem、code context、options 與 scope | `/opsx:explore` | 可以停止或準備提案；Department profile 不寫 artifact/code |
| 對已決定要做的 behavior change 選方案並形成 approved design | `superpowers:brainstorming` | Design 經 Human approval；已有等價 approved design 才可跳過 |
| 讓下一個 session、AI 或 Engineer 依同一份 why／what／how／tasks 繼續工作 | OpenSpec `/opsx:propose` or `new/continue` | 建立可維護的 Change；OpenSpec 也能 apply/verify，但 TDD、code review、runtime tests 仍由 engineering disciplines/evidence 承接 |

| If… | Use… |
|---|---|
| 不知道系統全貌或 domain language | manual `system-research` |
| 知道需求，但不知道 code 在哪裡、如何流動 | manual `codebase-research` |
| 重要規則在使用者/operator 腦中 | `grill-me` |
| 有 problem，但還沒有 plan；需要比較 options/scope | `/opsx:explore` |
| 已清楚要做什麼，需要 durable why/what/how/steps agreement | `/opsx:propose`；複雜工作用 `new/continue` |
| 已有文件但不確定是否完整/一致 | `grill-with-docs` |
| 符合 §4.2 canonical System Design trigger | 進行 System Design，完成 System Design Review |
| 已有 current-state evidence，且明確要找 architecture improvement／refactor opportunities | Optional `improve-codebase-architecture`；Human 選定 candidate 後再進 System Design 或 Feature/Detailed Design |
| 要新增或改變 behavior，且尚無 equivalent approved design | `brainstorming`，design approved 後才能 plan/implement |
| P1 Feature / Approved Design 包含多個獨立 outcome | `to-tickets`；每張 P0 標示 `Blocked by` |
| 未採用 OpenSpec 的單一 P0 即將執行，且 multi-step、high-risk 或 complex | `writing-plans`；簡單單一步驟 P0 可 inline |
| OpenSpec Change 的下一個 task 顆粒過粗 | 在 `/opsx:apply` 中直接於 `tasks.md` 展開巢狀子項；不使用 `writing-plans` |
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
| OpenSpec Change Container | Not at P3; child P1/P0 only | Not Epic hierarchy; child P1/P0 only | 當 change context 必須交接／維護時使用 | P0 僅在相同需求下使用 |
| Decomposition | Epic/Wave Map | Feature Map | P0 tickets + `Blocked by` | Execution tasks / plan steps |
| Implementation Plan | None at this level | None at this level | Not Feature-wide; JIT per P0 | Triggered for multi-step/risky/complex；inline for simple |
| Tests / Executable Evidence | Strategy + rollup | Integration/NFR rollup | Feature tests | Targeted tests |
| Review Record | Product/architecture decisions | Epic/design review | PR review | Risk-based review |
| Release / Migration Evidence | Required | Required when released | Required when deployed | Existing process |

**Document minimization rule：同一 artifact 可以同時滿足多個欄位；不要為了表格完整建立空文件。**

### 12.1 Reference Tracker Mapping

Canonical Azure DevOps／GitLab mapping 只維護於 [Framework §5.7](02_Framework.md#57-tracker-reference-mapping)。本 Playbook 使用 P3／P2／P1／P0／Execution Layer 的 Framework semantics；Team tracker 名稱不同時，reference canonical table，不複製或重新定義 hierarchy。

### 12.2 Artifact Placement — Information, Not File Format

**Artifact requirement defines required engineering information and evidence, not a mandatory file format.**

| Information / Evidence | Reuse First |
|---|---|
| Problem、scope、acceptance、risk、P0 type | Existing Epic／Feature／PBI／Issue |
| Research/system understanding | Work item attachment/link、architecture knowledge base、repository guidance |
| Durable change/design agreement | Existing design/RFC/ADR；OpenSpec when adopted and longevity requires it |
| P0 slices、blockers、frontier | Existing backlog/tracker |
| Per-P0 execution plan | P0 work item／Task child item、OpenSpec `tasks.md`、PR description or linked plan |
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
codebase-research only if existing behavior/change boundary is unknown
→ /opsx:explore (if fuzzy)
→ System Design + System Design Review (if triggered)
→ choose the design SSOT:
    existing ticket/design SSOT → brainstorming / Team equivalent when needed
    durable handoff needed → /opsx:propose or new/continue
→ grill-with-docs (risk-based)
→ if multiple independent outcomes: to-tickets → P0 slices + Blocked by
→ each bounded P0: use OpenSpec tasks.md when adopted;
                    otherwise inline or triggered writing-plans
→ worktree + TDD + selected execution skill;
  OpenSpec Change enters through /opsx:apply
→ code review + verification-before-completion
→ /opsx:sync → /opsx:archive only when OpenSpec is used
```

### Scenario B —「我要修一個 Bug」

```text
reproduce
→ systematic-debugging
→ regression test
→ confirm P0 acceptance + Blocked by
→ if OpenSpec is used: use tasks.md and expand a coarse task in place during /opsx:apply
  otherwise: inline plan, or writing-plans if multi-step/complex
→ minimal fix with TDD
→ review
→ verification-before-completion
```

### Scenario C —「我要開一個 Greenfield Product」

```text
first unknown:
  domain/system 不清楚 → system-research
  Owner decisions 不清楚 → grill-me
→ /opsx:explore only while options/scope remain fuzzy
→ product/domain design
→ System Design; grill-with-docs if useful
→ epic map / MVP plan
→ each P1 Feature：若含多個 slices 才 Design → to-tickets → P0 execution；否則直接作為一個 P0
→ scoped OpenSpec Change only at coherent P1/P0
```

### Scenario D —「我要做 Legacy Modernization / Migration」

```text
select by first unknown:
  system/domain → system-research
  existing behavior/change boundary → codebase-research
  hidden owner/operator rules → grill-me
→ as-is model + behavior catalog + characterization baseline
→ /opsx:explore only while migration options/scope remain fuzzy
→ target System Design + migration design
→ grill-with-docs + System Design Review
→ wave plan
→ each wave decomposes to P1 Features, then expand/migrate/contract P0 slices
→ scoped OpenSpec Change only where P1/P0 context must survive handoff
→ parity/reconciliation/cutover validation
```

### Scenario E —「需求不清楚，但主管要我快點做」

```text
grill-me if Owner decisions are still implicit
→ codebase-research if existing behavior is unknown
→ /opsx:explore if change intent/options/scope remain fuzzy
→ owner confirms direction
→ /opsx:propose only when the context must survive handoff
→ otherwise use the existing ticket/design/PR chain
```

快不是跳過 Research/Design；快是使用正確 skill，把模糊與 rework 提前消除。

### Scenario F —「我要寫 RFC / Architecture Decision」

```text
select system-research or codebase-research by the missing evidence
→ /opsx:explore only while options/scope remain fuzzy
→ System Design or Feature/Detailed Design by scope
→ grill-with-docs
→ approved proposal/spec/design + ADR
```

Minimum pack：Context Summary、Current State、Problem Statement、Alternatives/Trade-offs、Grill Result、ADR/Design Decision。

### Scenario G —「我要做 Incident Review 並防止再發」

```text
system-research + systematic-debugging
→ timeline + proven root cause
→ grill-with-docs on incident evidence/runbook
→ corrective actions
→ updated test/alarm/runbook
→ verification-before-completion
```

### Scenario H —「我要設計新系統或跨系統 Capability」

```text
select system-research or codebase-research by the missing evidence
→ Research Brief / Current System Model
→ /opsx:explore only while architecture options/scope remain fuzzy
→ System Design
→ grill-with-docs
→ System Design Review
→ ADRs + Epic/Feature Map
→ approved P1 Features：多個 slices 才 use to-tickets；單一 bounded slice 直接進 P0；P0 uses JIT planning when triggered
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

1. **不要每個 P0 都跑全部 capabilities／skills。** 只使用當前 stage 的 active default 與必要 supporting skill；已完成 equivalent mapping 的 Team 可使用等價 implementation。
2. **不要用 `writing-plans` 補救沒有 approved design 或多 P0 slicing。** 前者回到 Research/Design；只有 P1 確實包含多個獨立 outcome 時才用 `to-tickets`。
3. **不要用 brainstorming 取代 codebase evidence。** Existing system 先做 codebase research。
4. **不要用大量文件取代 decision。** Artifact 必須服務 handoff、review 或 evidence。
5. **不要因 P3 就一次設計所有 Features。** 先建立 product/epic boundaries，逐層展開。
6. **不要因 P0 就跳過 root cause 或 tests。** 深度可以輕，閉環不能消失。
7. **不要讓 skill workflow 取代現有 SDLC authorization。** E3 actions 仍由既有 owner/process 控制。
8. **OpenSpec Change 只有一份 `tasks.md`。** `/opsx:apply` 依它取 task、打勾與交接；不得使用 `writing-plans` 或建立第二份 plan/ledger。粗 task 直接在原檔做 JIT breakdown。
9. **不要在 Explore 裡偷偷 implementation。** `/opsx:explore` 維持 E0；確認 change intent 後才進 proposal/change package。
10. **不要把 System Design 變成所有工作的 mandatory ceremony。** P3/P2 required；P1 risk-triggered；P0 通常使用 micro-design。
11. **不要複製 architecture SSOT。** P3/P2 System Design 存在既有 Product/Architecture artifact；OpenSpec 只引用或記錄 bounded delta。
12. **不要先替整個 Epic 建立 implementation plan。** 先拆 Features；P1 只有包含多個獨立 outcome 時才用 `to-tickets`；未採用 OpenSpec 的單一 P0 才按需觸發 `writing-plans`。
13. **不要把 Task 或 OpenSpec Change 當成 P0 同義詞。** Task 位於 Execution Layer；Change 是 P1/P0 scope-dependent container。
14. **不要建立平行 AI SDLC。** Golden Stage 要 mapping 到既有 backlog、design、PR、test、release 或 incident flow，不是再開一條 process。
15. **不要把 Golden Stage 固定成 Team 統一 phase。** 一個 activity 可承載多個 Stages；一個 Stage 也可跨 activity／Sprint。
16. **不要由 Department 統一所有 Team templates。** Department 定 contract/quality bar；Team 定格式、欄位與 local workflow。
17. **不要忽略既有十個以上 pilots，重新要求證明。** 先 consolidation、選 canonical cases，其餘進 Case Library。
18. **不要把 `grill-me`、`/opsx:explore`、`brainstorming` 與 OpenSpec 全部串成固定前置流程。** 先處理第一個還沒搞清楚的問題；問題改變後才換下一個 skill。只有需要保存 why／what／how／tasks 供後續接手時，才加入 OpenSpec。

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
- P1 delivery planning 只有在需要多個 P0 時使用 `to-tickets`；單一 bounded P1 可直接作為一張 P0。P0 implementation breakdown 必須先有一張明確 P0；已採用 OpenSpec 時只用同一份 `tasks.md`，未採用時才用 inline／triggered `writing-plans`。

### Ready for Implement

- P0 outcome、acceptance、`Blocked by` 與 execution readiness 清楚。
- 已採用 OpenSpec 時，`tasks.md` bounded and executable；未採用時，triggered JIT plan bounded and executable，簡單 P0 有 inline steps/test direction。
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

- `README.md`：依角色導向正確 artifact 與 SSOT；Engineer 以本 Playbook 對應章節為必要 execution SSOT，第一次接觸可選讀 `04`，routing ambiguity 才查 `05`。
- `guides/04_Framework_Overview.md`：呈現 Golden Flow 的單一 Engineer mental model；區分新工作的完整 initial routing 與執行中的 Stage／Next Move refresh。
- `guides/05_Decision_Tree.md`：開頭提供 compact router；不要求每項工作先套完所有 taxonomy，再按需進入詳細分類章節。
- `training/06_Training_Presentation.pptx`：用真實 scenarios 教會 Engineer 如何開始。
- `reference/Golden_Skill_Registry.md`：管理 skill source、environment、installation、invocation、status 與 fallback。

Supplements 不新增新方法；若 supplements 暴露缺口，先修正 Framework 或 Golden Playbook，再重新衍生。

Framework Overview、Decision Tree 與 Training Presentation 必須共同呈現：

- `P3 → P2 → P1 → P0 PBI/User Story → Execution Layer`，且 Task 不列為 Work Level。
- Plan stage 分成兩個問題：多個獨立 outcome 的 P1 才用 `to-tickets`／Team equivalent 切 P0；implementation breakdown 已採用 OpenSpec 時只用 `tasks.md` 並在原檔就地展開，未採用時才由 inline plan／triggered `writing-plans` 承接。
- P0 types、`Blocked by`、execution frontier，以及 Spike 的 evidence/decision outcome。
- OpenSpec Change 是 P1/P0 scope-dependent durable container；`/opsx:explore` 仍為 E0/no-stakes。
- System Design 仍在 Design stage，保留三個 Human Gates，不新增 universal gate。
- Tracker 只做 reference mapping；GitLab Milestone/Iteration 不進入 hierarchy。
- Golden Stages 是可攜式 decision states，不是部門統一 SDLC phases；Team workflow 與 templates 由 Team 擁有。
- Golden Flow 是唯一 Engineer workflow；新工作先完成 Six Golden Questions，執行中更新 Current Stage／Next Move，context 改變時完整重判。七段 responsibility coverage 不進入 Engineer-facing supplements。
- `Understand → Challenge → Execute → Evidence` 是每個 Stage 的 AI 基本功，不呈現為第二套 lifecycle。
- 首先問 existing work location 與最大未知/風險，再選 required engineering activity／supporting skill、artifact placement 與 gate；只有會改變決策時才補 Work Level、Archetype 或完整 Control Profile。
- Research 先採不需安裝的 manual capability defaults；Candidate implementation 核准後才可取代。其他 Golden defaults 與 Team equivalents 仍需完成 capability、input/output、stop condition、gate 與 evidence mapping。
- Engineer start path 先呈現 Six Golden Questions 與 Golden Flow；OpenSpec、Superpowers、`to-tickets`、`writing-plans` 只在 Current Stage 內出現。是否採用 OpenSpec 只作 artifact／execution selection，不成為另一個外層 mental model。
- Mixed mode 的連接點寫成可執行 contract：`/opsx:apply` 依唯一的 `tasks.md` 決定目前做哪個 task；`test-driven-development` 決定該 task 如何以 RED → GREEN → REFACTOR 完成。粗 task 只在原檔展開子項；改變做法才走 `/opsx:update`。
- 既有十個以上 pilot cases 是 evidence base；選 3–5 canonical cases，其餘進 Case Library。

Decision Tree 的 opening router 同時擔任日常 quick reference；不另行維護重複的 `07` content SSOT。若需要 PDF／PNG handout，應由相同 source 產生。

## Appendix D — Change Log

| Version | Change |
|---|---|
| v1.12 | Engineer-entry correction：入口由 Fast／Durable route 改回 Six Golden Questions；Golden Flow 定位 Current Stage，skills/tools 只在 Stage 內選擇。Plan 明確分開 P1→P0 delivery decomposition 與 Change／P0→tasks implementation breakdown；OpenSpec `tasks.md` 保留 task breakdown 能力、P1-scoped Change reference P0 IDs，並維持 single-ledger rule。 |
| v1.11 | Adoption simplification：`to-tickets` 改為只有 P1 包含多個獨立交付 outcome 時才使用；單一 bounded P1 直接作為一個 P0，走 Superpowers／Team equivalent route。同步更新 Plan、P1 Playbook、Golden Matrix 與 scenarios。 |
| v1.10 | Durable execution correction：OpenSpec `tasks.md` 明定為唯一 task ledger；`/opsx:apply` 依它取 task、執行、打勾與交接，Durable Change 禁止使用會另建 `docs/superpowers/plans/` 的 `writing-plans`。新增粗 task 的 in-place JIT breakdown 規則、Engineer checkpoint、before/after 範例與邊界判準：只長子項是 JIT，改變做法須 `/opsx:update` 並按 scope/risk 判斷 Change Gate。 |
| v1.9 | Engineer adoption simplification：將入口由 framework capability history 改成兩條可直接執行的 route。Fast Delivery 明示 Superpowers end-to-end；Complex/Durable Change 明示 OpenSpec proposal/specs/design/tasks → Change Gate → `/opsx:apply`，每個 task 套用 Superpowers TDD，最後 review／verification／`/opsx:verify`／sync/archive。Discovery 降為 pre-route，新增 copyable apply-session execution contract 與 Spec-to-TDD handoff table。 |
| v1.8 | Responsibility/flow correction：新增 Responsibility Ownership Map，明確 OpenSpec 擁有 Spec-Driven Development/change traceability、Superpowers 提供 TDD-centered engineering disciplines。將 combined workflow 改為 Fast Delivery、Durable Change、Discovery First 三條實際 route；mixed mode 固定單一 spec/design/tasks owner、execution entry 與 task ledger，並保留 `/opsx:apply`／`verify` 與 Superpowers design/plan capabilities 的真實邊界。 |
| v1.7 | Capability-routing correction：依第一個還沒搞清楚的問題選下一個 skill；`grill-me` 訪談、`/opsx:explore` 探索、`brainstorming` 形成 approved design、OpenSpec 保存可交接的 why／what／how／tasks。Team profile 是 shared convention；OpenSpec 與 upstream Superpowers 混用前必須核准 artifact integration，否則只搭配不重複建文件的 execution skills。 |
| v1.6 | Simplicity/effectiveness correction：區分 initial routing 與 continue routing；新工作完整回答 Six Golden Questions，執行中通常只更新 Current Stage／Next Move，context 改變時再完整重判。Research 改用 rollout-ready manual `system-research`／`codebase-research` capability defaults；candidate skill 不再冒充 active default。移除重複 tracker table 與 E3 chain，改連 canonical Framework sections。 |
| v1.5 | Adoption navigation correction：新增 Root README role paths 與 Golden Skill Registry；Engineer 以本 Playbook 對應章節為必要 execution SSOT，Overview 為 optional visual summary，routing ambiguity 才查 Decision Tree。Decision Tree opening router 同時擔任 quick reference，不再建立獨立 `07` content SSOT。 |
| v1.4 | Engineer mental-model correction：Golden Flow + Six Golden Questions 成為唯一 Engineer workflow；AI Work Loop 改為每個 Stage 的 AI 基本功。移除七段 formal lifecycle mapping，Skill policy 改為 required discipline + Golden default + approved equivalent mapping，避免只會 vibe coding 的 Engineer 在沒有方法下自行選擇。 |
| v1.3 | SDLC integration correction：Golden Stages 保留為穩定的 portable engineering decision states，不綁定單一 Team SDLC。加入 existing work location router、每個 Stage 的 typical touchpoints／artifact location／decision owner／process trigger、artifact placement、Team-owned workflow/templates、Agile/Sprint DoR/DoD、E3 existing authorization 與既有 pilot consolidation。 |
| v1.2 | Semantic correction：P0 改為 PBI/User Story vertical slice；Task 移至 Execution Layer；OpenSpec Change 改為 P1/P0 scope-dependent container；加入 `to-tickets` P1 → P0、per-P0 JIT `writing-plans`、blocker frontier、wide-refactor pattern 與 Azure DevOps/GitLab reference mapping。Golden Flow、三個 Human Gates 與 System Design trigger 不變。 |
