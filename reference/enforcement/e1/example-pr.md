# E1 Example PR

這是 copy/paste example，不是新 mandatory template。保留 Team 原本 PR template，只加入需要的 decision information。

## Pass Example — Non-P0

```markdown
## Work item

Existing tracker item: ABC-123

## Scope and evidence

- Reviewed scope: payment retry behavior
- Evidence: CI run / test report / design link

## Human decision

Reviewer approves the current PR and applies `gate:pass`.
```

GitHub approval 已提供 Human Owner、decision time 與 reviewed commit；PR 本身提供 scope 與 evidence links，不要重複填一張表。

## Conditional Pass Example — Non-P0

```markdown
## Work item

Existing tracker item: ABC-456

## Scope and evidence

- Reviewed scope: staged migration batch 1
- Evidence: CI run / reconciliation report / rollback evidence

Condition tracking: #789
```

Reviewer approves current PR and applies `gate:conditional`。Issue `#789` 記錄未完成 condition、owner 與 due/exit condition。

## Rework

Apply `gate:rework`；workflow blocks merge until findings are resolved and the Human Reviewer changes the decision。

## P0

P0 只沿用既有 PR approval，不加 gate label、額外 section 或新欄位。Workflow 的 `P0_LABELS` 只能 mapping Team 已存在的 metadata。
