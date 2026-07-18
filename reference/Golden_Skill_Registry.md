# Golden Skill Registry

> Status: Active reference
> Purpose: Golden skill provenance、environment mapping、installation、invocation 與 fallback SSOT
> Last verified: 2026-07-18

本 Registry 解決「Playbook 指定了 Golden default skill，但 Engineer 不知道來源、是否可用或如何啟動」的 adoption gap。

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
| **Verified source** | Source 與用途已對照 upstream；仍需 Team 確認 approved version／environment |
| **Candidate mapping** | 名稱與用途相符，但尚未由 Department 核准為 installable Golden default |
| **Logical capability** | Department capability alias，不假設存在同名 skill |
| **Source unresolved** | Playbook 使用了 alias，但 repository 尚未記錄權威 implementation source |

## Registry

| Capability / Alias | Type / Status | Source | Environment / Install | Invocation | Expected Output / Stop Condition | Fallback |
|---|---|---|---|---|---|---|
| `understand-anything` | Installable candidate / **Candidate mapping** | [Lum1104/Understand-Anything](https://github.com/Lum1104/Understand-Anything) | Codex candidate install: `curl -fsSL https://raw.githubusercontent.com/Lum1104/Understand-Anything/main/install.sh \| bash -s codex`；Claude Code uses the upstream plugin marketplace；Team approval required | Upstream uses `/understand` and related commands | Knowledge/system map、glossary、flow、unknowns；stop when boundary、critical concepts and unknowns are explainable | Ask the agent to perform read-only cross-document/system research and produce the same minimum output |
| `codebase-research` | Department alias / **Source unresolved** | **Maintainer must record the approved implementation; do not infer one from similarly named public skills** | No approved install instruction in this repository | Use the environment's approved repository-research capability | Code map、entry points、call/data flow、existing patterns、evidence links；stop when change boundary is located | Read-only inspect code、tests and history; cite files/symbols and produce the required Code Map |
| `grill-me` | Installable skill / **Verified source** | [mattpocock/skills — grill-me](https://github.com/mattpocock/skills/blob/main/skills/productivity/grill-me/SKILL.md) | `npx skills@latest add mattpocock/skills`；select `grill-me` and `setup-matt-pocock-skills` for supported Agent Skills harnesses | `/grill-me` | Structured questions、decisions、assumptions、examples、open questions；stop when material tacit knowledge is explicit | Ask the agent to interview the owner 1–3 questions at a time until material decisions and examples are confirmed |
| `grill-with-docs` | Installable skill / **Verified source** | [mattpocock/skills — grill-with-docs](https://github.com/mattpocock/skills/blob/main/skills/engineering/grill-with-docs/SKILL.md) | Same Matt Pocock installer; run `/setup-matt-pocock-skills` once per repo | `/grill-with-docs` | Evidence-based findings、missing cases、decision closure and updated durable docs when approved | Review the named artifacts against goals、constraints、examples、failure modes and contradictions; produce findings with evidence and decision owner |
| `to-tickets` | Installable skill / **Verified source** | [mattpocock/skills — to-tickets](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) | Same Matt Pocock installer; configure tracker through `/setup-matt-pocock-skills` | `/to-tickets` | P0 tracer-bullet tickets、acceptance、`Blocked by`、execution frontier；stop when each slice is narrow、complete and independently verifiable | Decompose the approved P1 into vertical P0 slices using the same ticket and blocker contract |
| `system-design` | Department alias / **Logical capability** | Defined by [`03_Golden_Engineering_Playbook.md`](../03_Golden_Engineering_Playbook.md); no single installable source assumed | No installation | Invoke the approved local bundle | System context、boundaries、runtime/data flow、contracts、NFR、failure/recovery/observability、ADRs、decomposition；stop at accountable review | Evidence research → option exploration → design refinement → adversarial document review → Architect/Tech Lead review |
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

1. Resolve and approve the authoritative `codebase-research` implementation before calling it an installable Golden default.
2. Confirm whether `Lum1104/Understand-Anything` is the intended Department implementation or only an approved equivalent.
3. Record approved versions or commit SHAs instead of tracking floating `main`／`latest` for controlled enterprise rollout.
4. Verify installation and invocation separately in each supported environment.
5. Update this Registry whenever Playbook aliases, sources or upstream commands change.

External install commands are recorded for traceability, not blanket authorization. Engineers must follow existing company policy for third-party code、plugins、data access and AI tooling.
