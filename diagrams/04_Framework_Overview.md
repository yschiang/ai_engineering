# AI-Native Software Engineering Framework — One-Page Overview

> Version: v1.4 Candidate  
> Status: Ready for Sponsor Review  
> Derived from: `02_Framework.md` v1.6 Baseline + `03_Golden_Engineering_Playbook.md` v1.4 Baseline  
> Purpose: Engineer and management visual entry point; supplement only

---

## The Operating Model

**在 Team 既有 workflow 裡，用 Six Golden Questions 定位，再沿著唯一的 Golden Flow 處理下一個工程問題。**

Golden Stages 是 portable engineering decision states，不是所有 Team 必須採用的固定 SDLC phases。Team 擁有 local activities、artifact placement 與 templates；Department 擁有 minimum contract 與 quality bar。

```mermaid
flowchart TB
  W["Team-owned Existing Workflow / System of Record\nTicket · Design · PR · Test · Release · Incident"]
  C["Six Golden Questions\nLocation · Level · Archetype · Stage · Control · Next Move"]
  subgraph F["Golden Flow"]
    direction LR
    R["1 Research\nUnderstand · Explore · Define"] --> D["2 Design\nSystem Design* · Feature Design · Challenge"] --> P["3 Plan\nP1→P0 slices · P0→tasks JIT"] --> I["4 Implement\nTDD · bounded change"] --> V["5 Validate\nReview · fresh evidence"]
  end
  W -. "apply where needed" .-> C
  C --> R
  V --> O["Release & Operate\nObserve · Recover · Learn"]
  O -. "Learning loop" .-> R
```

`*` System Design：P3/P2 required；P1 risk-triggered；P0 normally skip。

- **AI 基本功 in every Golden Stage**：先 Understand、Challenge，再 Execute 並留下 Evidence；它不是第二套 lifecycle。

---

## 1. Classify Before Acting

| Decision | Choose | Determines |
|---|---|---|
| **Work Level** | P3 Product/Program → P2 Epic → P1 Feature → P0 PBI/User Story | Delivery decomposition、artifact depth、review owner |
| **Execution Layer** | Task → Plan Step → Commit（位於 P0 下方） | Implementation execution；不是 Work Level |
| **Archetype** | Greenfield · Legacy Modernization/Migration · Standard Delivery | Research/Design focus |
| **Control Profile** | System Criticality × L0–L3 Change Risk × E0–E3 AI Execution Mode | Rigor、authorization、evidence strength |

AI Execution Mode：**E0 Observe → E1 Propose → E2 Change → E3 Act**。

P0 types：**User Story · Engineering Story/Enabler · Bug · Spike**。每張 P0 都有 acceptance 與 `Blocked by`；無 blocker 的 P0 構成 execution frontier。Spike 以 evidence/decision outcome 驗證。

**System Design trigger**：P3/P2 required；P1 在 cross-boundary/contract/data、重大 NFR、novel architecture 或 L2–L3 時 triggered；P0 normally skip，architecture impact 則升級。System Design Review 是 **Change Gate implementation**，不是新 gate。

---

## 2. Golden Stage Contract

| Stage | Required Capability / Golden Defaults | Minimum Artifact | Human Gate |
|---|---|---|---|
| **Research** | Evidence-backed understanding；defaults：`understand-anything` · `codebase-research` · `grill-me` · `/opsx:explore` | Research / Understanding Brief | **Understanding Gate**：current state、problem、scope、unknowns 清楚 |
| **Design** | Select/challenge design；defaults：triggered `system-design` · `brainstorming` · `/opsx:propose` · `grill-with-docs` | System Design Pack when triggered + Feature Design / OpenSpec proposal/specs/design | **Change Gate**：design、risk、decomposition 可接受 |
| **Plan** | Delivery/JIT decomposition；defaults：`to-tickets` P1 → P0；triggered `writing-plans` P0 → tasks | P0 backlog + blockers；JIT executable plan when needed | **Change Gate**：slices 獨立可驗證、plan bounded |
| **Implement** | Test-first bounded execution；defaults：`/opsx:apply` + worktree + TDD + execution skill | Code/config/migration + tests + task ledger | Plan compliance + targeted verification |
| **Validate** | Review + fresh verification；defaults：code review · `/opsx:verify` · `verification-before-completion` | Validation Record / PR evidence | **Evidence Gate**：claims 有 fresh evidence |

---

## 3. Capability Responsibility

| Capability | Owns |
|---|---|
| **Research skills** | Domain、system、codebase、tacit-knowledge evidence |
| **OpenSpec** | Scoped P1/P0 durable agreement and archive |
| **`to-tickets`** | Approved P1 → P0 tracer bullets、blockers、frontier |
| **Superpowers** | Design、per-P0 JIT planning、TDD、review、verification discipline |
| **Human Owner** | Direction、trade-offs、authorization、risk acceptance、release |

SSOT rule：P3/P2 architecture 存在 Product/Architecture artifacts；OpenSpec Change 是 P1/P0 scope-dependent container，引用或記錄 bounded delta。`/opsx:explore` 維持 E0/no-stakes。

---

## 4. Three Gates, One Accountability Model

| Gate | Pass evidence |
|---|---|
| **Understanding** | Current state、problem、scope、unknowns are evidence-backed |
| **Change** | Design、risk、P0 decomposition and triggered plan are acceptable |
| **Evidence** | Acceptance、affected risks、release/recovery claims have fresh evidence |

所有 work 都維持三項 Universal Controls：**Clear Intent · Human Accountability · Risk-based Evidence**。

---

## Engineer Start in 60 Seconds

1. **Current Work Location**：工作目前在哪個 existing activity／system of record？
2. **Work Level**：P3、P2、P1 或 P0？
3. **Archetype**：Greenfield、Modernization/Migration 或 Standard Delivery？
4. **Current Golden Stage**：最大的未知或風險屬於 Research、Design、Plan、Implement、Validate 哪一類？
5. **Control Profile**：需要多嚴謹、AI 能做到哪裡？
6. **Next Move**：採用哪個 Golden default skill、留下什麼 evidence、由誰完成 gate decision？

新手與尚未建立 local practice 的 Team 直接採用 Golden defaults；成熟 Team 只有在完成 equivalent capability、input/output、stop condition、gate 與 evidence mapping 後才替換。

Tool/tracker routing details：see `05_Decision_Tree`。

> **Outcome：更快理解正確的問題、做出更好的 engineering decision，並用足夠 evidence 安全交付。**
