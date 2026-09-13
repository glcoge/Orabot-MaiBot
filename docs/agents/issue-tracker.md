# Issue tracker: 本地 Markdown（Local Markdown）

本仓库的 issue 和 spec 作为 `.scratch/` 下的 Markdown 文件。

## 约定

- 一个功能一个目录：`.scratch/<feature-slug>/`
- spec 是 `.scratch/<feature-slug>/spec.md`
- 实现 issue 每单一个文件，在 `.scratch/<feature-slug>/issues/<NN>-<slug>.md`，从 `01` 起编号，绝不用合并的单一工单文件
- triage 状态记在每个 issue 文件顶部附近的 `Status:` 行（见 `triage-labels.md` 的角色字符串）
- 评论和对话历史追加到文件底部的 `## Comments` 标题下

## 当 skill 说"发布到 issue tracker"

在 `.scratch/<feature-slug>/` 下新建一个文件（按需创建目录）。

## 当 skill 说"抓取相关工单"

读引用路径处的文件。用户通常会直接传路径或 issue 编号。

## Wayfinding 操作

被 `/wayfinder` 使用。地图是一个文件，每个工单一个 **子文件**。

- **地图**：`.scratch/<effort>/map.md`（Notes / Decisions-so-far / Fog 正文）。
- **子工单**：`.scratch/<effort>/issues/NN-<slug>.md`，从 `01` 起编号，问题在正文中。`Type:` 行记工单类型（`research`/`prototype`/`grilling`/`task`）；`Status:` 行记 `claimed`/`resolved`。
- **阻塞**：顶部附近的 `Blocked by: NN, NN` 行。一张工单在其列出的每个文件都 `resolved` 时 unblocked。
- **Frontier**：扫 `.scratch/<effort>/issues/` 找开放、未阻塞、未 claim 的文件；编号最小者胜。
- **Claim**：设 `Status: claimed` 并在任何工作前保存。
- **Resolve**：在 `## Answer` 标题下追加答案，设 `Status: resolved`，然后向 `map.md` 的 Decisions-so-far 追加一个上下文指针（概括 + 链接）。