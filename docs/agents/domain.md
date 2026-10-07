# 领域文档（Domain Docs）

工程 skills 在探索代码库时应如何消费本仓库的领域文档。

## 探索前，先读这些

- 仓库根的 **`CONTEXT.md`**，或
- 若仓库根有 **`CONTEXT-MAP.md`**：它指向每个上下文一个 `CONTEXT.md`。读每个与主题相关的。
- **`docs/adr/`**：读触及你即将工作区域的 ADR。多上下文仓库里也查 `src/<context>/docs/adr/` 的上下文特定决策。

若这些文件都不存在，**静默继续**。别标它们的缺席；别建议 upfront 创建它们。`/domain-modeling` skill（经由 `/grill-with-docs` 和 `/improve-codebase-architecture` 到达）在术语或决策真正被解决时才惰性创建它们。

## 文件结构

单上下文仓库（多数仓库）：

```
/
├── CONTEXT.md
├── docs/adr/
│   ├── 0001-event-sourced-orders.md
│   └── 0002-postgres-for-write-model.md
└── src/
```

多上下文仓库（根存在 `CONTEXT-MAP.md`）：

```
/
├── CONTEXT-MAP.md
├── docs/adr/                          ← 系统级决策
└── src/
    ├── ordering/
    │   ├── CONTEXT.md
    │   └── docs/adr/                  ← 上下文特定决策
    └── billing/
        ├── CONTEXT.md
        └── docs/adr/
```

## 用术语表的词汇

当你的输出命名一个领域概念（在 issue 标题、重构提案、假设、测试名里），用 `CONTEXT.md` 里定义的术语。别漂移到术语表明确避免的同义词。

若你需要概念还不在术语表里，那是信号：要么你在发明项目不用的语言（重新考虑），要么有真实缺口（记给 `/domain-modeling`）。

## 标出 ADR 冲突

若你的输出与已有 ADR 矛盾，显式浮出而非静默覆盖：

> _与 ADR-0007（事件源订单）矛盾，但值得重开因为…_