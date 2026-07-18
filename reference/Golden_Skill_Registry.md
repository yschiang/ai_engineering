# Golden Skill Registry

> Status: Active reference
> Purpose: Golden skill provenance、environment mapping、installation、invocation 與 fallback SSOT
> Last verified: 2026-07-18

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
| `grill-me` | Installable skill / **Verified source** | [mattpocock/skills — grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) | `npx skills@latest add mattpocock/skills`；select `grill-me` and `setup-matt-pocock-skills` for supported Agent Skills harnesses | `/grill-me` | Structured questions、decisions、assumptions、examples、open questions；stop when material tacit knowledge is explicit | Ask the agent to interview the owner 1–3 questions at a time until material decisions and examples are confirmed |
| `grill-with-docs` | Installable skill / **Verified source** | [mattpocock/skills — grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) | Same Matt Pocock installer; run `/setup-matt-pocock-skills` once per repo | `/grill-with-docs` | Evidence-based findings、missing cases、decision closure and updated durable docs when approved | Review the named artifacts against goals、constraints、examples、failure modes and contradictions; produce findings with evidence and decision owner |
| `to-tickets` | Installable skill / **Verified source** | [mattpocock/skills — to-tickets](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) | Same Matt Pocock installer; configure tracker through `/setup-matt-pocock-skills` | `/to-tickets` | P0 tracer-bullet tickets、acceptance、`Blocked by`、execution frontier；stop when each slice is narrow、complete and independently verifiable | Decompose the approved P1 into vertical P0 slices using the same ticket and blocker contract |
| OpenSpec `/opsx:*` | CLI + agent commands / **Verified source** | [Fission-AI/OpenSpec](https://github.com/Fission-AI/OpenSpec) | Requires Node.js 20.19.0+; upstream quick start: `npm install -g @fission-ai/openspec@latest`, then `openspec init` in each project | Framework uses `/opsx:explore`, `/opsx:propose`, `/opsx:new`, `/opsx:continue`, `/opsx:ff`, `/opsx:apply`, `/opsx:verify`, `/opsx:sync` and `/opsx:archive`; availability depends on selected profile | Scoped proposal/spec/design/tasks、implementation alignment、sync/archive; stop or hand off according to the selected action | Use existing ticket／RFC／ADR／PR chain as the durable agreement SSOT; preserve the same why/what/how/tasks/evidence contract |
| Superpowers family | Plugin / **Verified source** | [obra/superpowers](https://github.com/obra/superpowers) | Codex App/CLI: install `Superpowers` from the official plugin marketplace; Claude Code: `/plugin install superpowers@claude-plugins-official`; follow upstream instructions for other harnesses | Skills normally trigger by task fit; explicit names depend on harness | See capability mapping below; each skill owns a specific stop condition | Apply the same engineering discipline manually and record evidence; do not claim the missing plugin was run |

## Superpowers Capability Mapping

| Framework capability | Superpowers implementation | Minimum contract |
|---|---|---|
| Feature / detailed design | `brainstorming` | Approved approach、options/trade-offs、behavior and test direction |
| P0 JIT planning | `writing-plans` | Exact files/interfaces、steps、tests、commands；no unresolved design decision |
| Workspace isolation | `using-git-worktrees` | Isolated worktree、known baseline、safe branch context |
| Test-first implementation | `test-driven-development` | Observe correct failure → minimal change → passing evidence |
| Multi-task execution | `executing-plans` or `subagent-driven-development` | Bounded task batches、review checkpoints、whole-change verification |
| Debugging | `systematic-debugging` | Reproduction、hypotheses、falsification、proven root cause |
| Review | `requesting-code-review` and `receiving-code-review` | Findings by severity、verified resolution or evidence-based disagreement |
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
