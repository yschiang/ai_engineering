# Golden Skill Registry

> Status: Active reference
> Purpose: Golden skill provenance、environment mapping、installation、invocation 與 fallback SSOT
> Last verified: 2026-07-19

本 Registry 解決「Playbook 指定了 Golden default capability，但 Engineer 不知道目前可用的執行方式、來源或如何啟動」的 adoption gap。**Candidate implementation 不得被寫成 active default**；尚未核准 installable skill 時，Department 以明確的 manual capability contract 作為可直接執行的 default。

Framework 仍然 tool-agnostic：required capability、input、output、stop condition、gate 與 evidence contract 由 Department 定義；本頁記錄目前採用或候選的 implementation。Team 使用 approved equivalent 時，必須提供同等 contract。

## Readiness Rule

使用任何 Golden default 前，確認：

1. Source 與版本可追溯。
2. 目前 agent／environment 已安裝或原生支援。
3. Engineer 知道如何 invoke。
4. Expected output 與 stop condition 清楚。
5. Skill 不可用時有 capability fallback，不因缺少特定工具而回到 open-ended vibe coding。

狀態定義：

| Status | Meaning |
|---|---|
| **Active capability default** | 不依賴安裝即可執行的 Department default；以明確 prompt／manual procedure、minimum output 與 stop condition 運作 |
| **Verified source** | Source 與用途已對照 upstream；仍需 Team 確認 approved version／environment |
| **Candidate mapping** | 名稱與用途相符，但尚未由 Department 核准為 installable Golden default |

## Registry

| Capability / Alias | Type / Status | Source | Environment / Install | Invocation | Expected Output / Stop Condition | Fallback |
|---|---|---|---|---|---|---|
| `system-research` | Manual research contract / **Active capability default** | Department contract：[Playbook §4.1 Research](../03_Golden_Engineering_Playbook.md#41-research) | 不需安裝；使用公司核准、能 read-only 存取指定文件／系統資訊的 agent 或既有工具 | 「對指定範圍做 read-only system research；區分 facts／assumptions／unknowns，產出 boundary、glossary、主要 flow、evidence references 與 open questions；不要修改任何 artifact」 | Knowledge/System Map、glossary、flow、unknowns；boundary、critical concepts 與 unknowns 可被解釋後停止 | 由 Engineer 使用既有文件、搜尋與訪談完成相同 contract，保留 source references |
| `codebase-research` | Manual repository-research contract / **Active capability default**；installable implementation 尚未核准 | Department contract：[Playbook §4.1 Research](../03_Golden_Engineering_Playbook.md#41-research)。Method reference：[HumanLayer `research_codebase.md` pinned source](https://github.com/humanlayer/humanlayer/blob/c2c31d656807cad9d389acfcbc19002733958218/.claude/commands/research_codebase.md)；portable snapshot：[NeverSight mirror pinned source](https://github.com/NeverSight/learn-skills.dev/blob/a446ce88373ee3784f04ce8fb6f3f2326230a525/data/skills-md/ferueda/agent-skills/research-codebase/SKILL.md) surfaced by this [LobeHub listing](https://lobehub.com/skills/neversight-skills_feed-research-codebase)。Mirror 只供 method review，不是 install source SSOT | Default 不需安裝；使用目前 environment 的 approved read-only repository inspection。第三方 skill 在 Team review、vendor/pin 與 environment verification 前不得安裝為 Golden default | 「對這個 repository 與指定問題做 read-only research；先讀指定 files，再按需要追 code、tests 與 history；引用 file／symbol／line evidence，產出 entry points、call/data flow、existing patterns、change boundary 與 unknowns；不要提出或實作改進」 | As-is Code Map／Research Brief、entry points、call/data flow、existing patterns、file/line evidence 與 change boundary；回答 research question後停止，不主動提出改進 | Engineer 以 repository search、code navigation、tests 與 history 手動完成相同 contract |
| `understand-anything` | Optional installable equivalent / **Candidate mapping**；不是 active default | [Lum1104/Understand-Anything](https://github.com/Lum1104/Understand-Anything) | Codex candidate install: `curl -fsSL https://raw.githubusercontent.com/Lum1104/Understand-Anything/main/install.sh \| bash -s codex`；Claude Code uses the upstream plugin marketplace；Team approval required | Upstream uses `/understand` and related commands | 必須至少滿足 `system-research` 的 Knowledge/System Map、glossary、flow、unknowns 與 stop condition | 使用 active `system-research` manual contract |
| `improve-codebase-architecture` | Installable skill / **Verified source**；Optional Design aid | [mattpocock/skills — improve-codebase-architecture](https://github.com/mattpocock/skills/blob/main/skills/engineering/improve-codebase-architecture/SKILL.md) | Same Matt Pocock installer；Team 必須一併 review/map `codebase-design`、`grilling`、`domain-modeling`、`CONTEXT.md` 與 ADR conventions | Manual invocation only：`/improve-codebase-architecture`；upstream sets `disable-model-invocation: true` | Temp HTML candidate report：architecture friction、before/after、recommendation strength、top recommendation；Human 選定 candidate 後停止並 hand off to formal design | 以 approved as-is evidence 手動進行 architecture assessment，產生 candidates／trade-offs／recommendation；Human 選定前不進 detailed design 或 implementation |
| `grill-me` | Installable skill / **Verified source** | [mattpocock/skills — grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) → [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) | `npx skills@latest add mattpocock/skills`；select `grill-me` and `setup-matt-pocock-skills` for supported Agent Skills harnesses | `/grill-me` | Structured questions、decisions、assumptions、examples、open questions；stop when material tacit knowledge is explicit。Skill 不保證 durable artifact；需要交接時寫回既有 SSOT | Ask the agent to interview the owner 1–3 questions at a time until material decisions and examples are confirmed；capture material decisions in the work item/design when needed |
| `grill-with-docs` | Installable skill / **Verified source** | [mattpocock/skills — grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) | Same Matt Pocock installer; run `/setup-matt-pocock-skills` once per repo | `/grill-with-docs` | Evidence-based findings、missing cases、decision closure and updated durable docs when approved | Review the named artifacts against goals、constraints、examples、failure modes and contradictions; produce findings with evidence and decision owner |
| `to-tickets` | Installable skill / **Verified source** | [mattpocock/skills — to-tickets](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) | Same Matt Pocock installer; configure tracker through `/setup-matt-pocock-skills` | `/to-tickets` | **Only when one P1 contains multiple independent outcomes**：產生 P0 tracer-bullet tickets、acceptance、`Blocked by`、execution frontier；stop when each slice is narrow、complete and independently verifiable | 若 P1 本身就是一個 bounded slice，直接視為一個 P0；手動依同一 contract 建立或確認 tracker item |
| OpenSpec `/opsx:*` | CLI + agent commands / **Verified source** | [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) | Requires Node.js 20.19.0+; upstream quick start: `npm install -g @fission-ai/openspec@latest`, then `openspec init` in each project | Framework uses `/opsx:explore`, `/opsx:propose`, `/opsx:new`, `/opsx:continue`, `/opsx:ff`, `/opsx:apply`, `/opsx:verify`, `/opsx:sync` and `/opsx:archive`; availability depends on selected profile | Scoped proposal/spec/design/tasks、implementation alignment、sync/archive; stop or hand off according to the selected action | Use existing ticket／RFC／ADR／PR chain as the durable agreement SSOT; preserve the same why/what/how/tasks/evidence contract |
| Superpowers family | Plugin / **Verified source** | [obra/superpowers](https://github.com/obra/superpowers) | Codex App/CLI: install `Superpowers` from the official plugin marketplace; Claude Code: `/plugin install superpowers@claude-plugins-official`; follow upstream instructions for other harnesses | Skills normally trigger by task fit; explicit names depend on harness | See capability mapping below; each skill owns a specific stop condition | Apply the same engineering discipline manually and record evidence; do not claim the missing plugin was run |

## Department Routing Policy

Registry 只回答「這個 capability 是否可用、如何啟動」，不取代 [Golden Playbook §1](../03_Golden_Engineering_Playbook.md#1-engineer-start-here--six-golden-questions) 與 [Decision Tree §6](../guides/05_Decision_Tree.md#6-choose-the-next-capability) 的 routing。Engineer 先完成 Six Golden Questions、定位 Current Stage；只有進入該 Stage 後才查本 Registry 選 implementation。

先用 Responsibility Ownership Map 避免按品牌拼 workflow：

| Responsibility | Default Implementation | Adoption Rule |
|---|---|---|
| Direction／roles | Existing Team workflow and owners | 不導入新的 virtual organization 作 Department prerequisite |
| Spec-Driven Development | OpenSpec；non-durable work 可用 existing ticket／design SSOT | OpenSpec 擁有 durable proposal/specs/design/tasks 與 change traceability |
| Engineering discipline | Superpowers／Team equivalent | 以 TDD-centered design、planning、debugging、review、verification disciplines 約束執行 |
| Execution orchestration | `/opsx:apply`、Superpowers execution 或 approved runner | 每個 change 一個 execution entry、一個 task ledger |
| Evidence／approval | CI、PR、tests、review、OpenSpec verify + Human Gate | Automation 產 evidence；Human Owner 作 decision |

> **OpenSpec owns Spec-Driven Development and change traceability. Superpowers enforces TDD-centered engineering disciplines.**

| Current Stage / Situation | Department Default |
|---|---|
| Research：P0/P1 要做什麼尚未清楚 | 依第一個未知選 research、`grill-me`、`/opsx:explore` 或 debugging；一次只選一個 |
| Design：需要跨 session／AI／Engineer 保存 why／what／how | Scoped OpenSpec proposal/specs/design；否則沿用 existing design SSOT + Superpowers／Team equivalent |
| Plan：P1 包含多個 independently deliverable outcomes | `to-tickets`／Team equivalent 建立 P0；若只有一個 bounded outcome，直接視為 P0 |
| Plan：已採用 OpenSpec，需要 implementation breakdown | 使用同一份 `tasks.md`；粗 task 在原檔展開，不使用 `writing-plans` |
| Plan：未採用 OpenSpec 的單一 P0 | simple work 用 inline plan；multi-step/high-risk/complex 才用 `writing-plans` |
| Implement／Validate | 依唯一 ledger 執行 TDD、debugging、review、fresh verification；OpenSpec change 由 `/opsx:apply` 進場 |

是否採用 OpenSpec，只作 Stage 內的 artifact／execution selection。它不是 initial routing，也不取代 Golden Flow。Team convention 可以指定 defaults，但 architecture/risk trigger、required capability、Human Gate 與 evidence quality 不可降低。

Department OpenSpec profile 採官方 `docs/explore.md` 的簡單邊界：`/opsx:explore` 是 E0/no-stakes，不建立 Change、不寫 artifacts、不修改 code；若 installed skill 提供 optional artifact capture，仍應交由 `/opsx:propose`、`/opsx:new`／`continue` 或既有 Change update flow 保存。OpenSpec Stores 仍為 beta，不列入 Golden default。

`/opsx:verify` 檢查 implementation/artifact alignment，CLI `openspec validate` 檢查 artifact validity；兩者都不取代 TDD、code review、runtime/NFR tests 或 release evidence。

官方 [OpenSpec team workflow](https://github.com/Fission-AI/OpenSpec/blob/main/docs/team-workflow.md) 建議把 Change 納入既有 branch/PR、固定 archive convention，並維持 one Change/one owner；[customization](https://github.com/Fission-AI/OpenSpec/blob/main/docs/customization.md) 支援 Team config/custom schemas，並列出 community `superpowers-bridge`。Bridge 不是 OpenSpec core 或 Department default；採用前必須 review/pin/verify。沒有 approved integration 時，由 OpenSpec 擁有 design/tasks，Superpowers 只使用不重複產生 design/plan 的 TDD/review/verification skills；不得同時維護 OpenSpec 與 `docs/superpowers/...` 兩份 SSOT。

## OpenSpec Capability Mapping

| Golden responsibility / stage | OpenSpec action | Minimum contract |
|---|---|---|
| Discovery / Research | `/opsx:explore` | E0、no-stakes exploration；不建立 Change、不寫 artifact/code；清楚後 stop 或交 propose/new |
| Durable agreement / Design | `/opsx:propose`，或 `/opsx:new` + `/opsx:continue`／`/opsx:ff` | Proposal 說 why、specs 說 what、design 說 how；通過 Change Gate |
| Implementation breakdown / Plan | OpenSpec `tasks.md` | 將 approved Change 拆成 executable tasks；粗 task 在原檔 JIT 展開。若 P1 Change 涵蓋多個 P0，只 reference tracker P0 IDs，不複製 acceptance／tasks |
| Bounded execution / Implement | `/opsx:apply` | 讀取 approved tasks、實作 change、按需要執行 tests、更新 task state；不自行改寫 approved scope |
| Alignment / Validate | `/opsx:verify` | 檢查 completeness、correctness、coherence 與 artifact/implementation alignment；不取代 TDD、code review 或 runtime/NFR evidence |
| Durable truth / Closure | `/opsx:sync` → `/opsx:archive` | 將 verified delta 同步回 specs/source of truth，關閉 Change 並保留 traceability |
| Artifact validity | CLI `openspec validate` | 檢查 artifact structure/consistency；不是 implementation verification |

OpenSpec Change 的 reference sequence：

```text
proposal/specs/design/tasks
→ Change Gate
→ /opsx:apply + selected engineering disciplines
→ /opsx:verify + PR evidence
→ Evidence Gate
→ /opsx:sync → /opsx:archive
```

這條 sequence 不要求把 Superpowers 全套再跑一次。沒有 approved bridge 時，只選 `test-driven-development`、`systematic-debugging`、`requesting-code-review`、`receiving-code-review`、`verification-before-completion` 等不建立第二份 design/plan 的 disciplines。

## Superpowers Capability Mapping

| Framework capability | Superpowers implementation | Minimum contract |
|---|---|---|
| Feature / detailed design | `brainstorming` | Approved approach、options/trade-offs、behavior and test direction |
| P0 JIT planning | `writing-plans` | Exact files/interfaces、steps、tests、commands；no unresolved design decision |
| Workspace isolation | `using-git-worktrees` | Isolated worktree、known baseline、safe branch context |
| Test-first implementation | `test-driven-development` | Observe correct failure → minimal change → passing evidence |
| Multi-task execution | `executing-plans` or `subagent-driven-development` | Bounded task batches、review checkpoints、whole-change verification |
| Debugging | `systematic-debugging` | Reproduction、hypotheses、falsification、proven root cause |
| Review | [`requesting-code-review`](https://github.com/obra/superpowers/blob/main/skills/requesting-code-review/SKILL.md) and [`receiving-code-review`](https://github.com/obra/superpowers/blob/main/skills/receiving-code-review/SKILL.md) | Validate owns review evidence；request may run after Implement tasks/checkpoints；feedback is verified before fix, reasoned pushback or closure |
| Completion evidence | `verification-before-completion` | Fresh command output supports every completion claim |
| Branch completion | `finishing-a-development-branch` | Tests pass and merge/PR/keep/cleanup decision is explicit |

## Maintainer Actions

1. Manual `system-research` 與 `codebase-research` capability contracts 是 rollout-ready defaults；不得要求 Engineer 等待第三方 skill 核准才能開始 Research。
2. Review the HumanLayer method reference and pinned NeverSight marketplace snapshot；若要採用為 installable implementation，建立 Department-owned reviewed copy、記錄 attribution/license、pin commit，並逐一驗證 environments。
3. Confirm whether `Lum1104/Understand-Anything` 應成為 `system-research` 的 approved equivalent；核准前不得在 Engineer path 稱為 default。
4. Record approved versions or commit SHAs instead of tracking floating `main`／`latest` for controlled enterprise rollout.
5. Verify installation and invocation separately in each supported environment.
6. Update this Registry whenever Playbook aliases, sources or upstream commands change.

External install commands are recorded for traceability, not blanket authorization. Engineers must follow existing company policy for third-party code、plugins、data access and AI tooling.
