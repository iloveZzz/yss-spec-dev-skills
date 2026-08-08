---
name: yss-valuation
description: Use when 用于 YSS valuation 组件、Excel/Csv 文件读取、Excel2SqlDDL、ImportFileJob、估值文件导入和区域条件解析排障。
---

> **消费项目上下文：** 本公开技能包不携带消费项目的 `AGENTS.md`、`CONTEXT.md` 或 `docs/`。文档中出现的这些路径均指可选的消费项目上下文；技能自身所需的参考资料、资源和脚本已随技能一同提供。

# yss-valuation

Use this skill for YSS 估值导入组件. Keep implementation grounded in the local project and resolvable YSS backend component source.

中文说明：本技能用于 YSS 估值导入组件。执行时优先读取源码索引，避免凭记忆猜类名、配置项或接入方式。

## Source Index First

- Backend source location is environment-specific; resolve it with `yss-source-index/references/source-location.md`.
- Generated index: `references/source-index.md`
- Component path hints: `yss-microservice-components/yss-component-valuation`

Read `references/source-index.md` as a path-hint index whenever the task depends on exact modules, annotations, auto configuration, properties, controllers, clients, repositories, DTOs, handlers, or troubleshooting.

## Workflow

1. Identify whether the task is valuation file import, Excel/CSV reading, Excel-to-DDL generation, table relationship extraction, or import job troubleshooting.
2. Read `references/source-index.md`, then inspect `Excel2SqlDDL`, `Excel2TableRelationship`, `ImportFileJob`, `FileReader`, `ExcelFileReader`, and `CsvFileReader`.
3. Use this component for valuation/data-middle file import and DDL derivation; load `yss-file` when the issue is generic file storage or parser infrastructure.
4. Validate file format, sheet/column mapping, encoding, and generated DDL before applying changes to a database.
5. Keep import jobs idempotent or clearly restartable when possible.

## Checklist

- Required dependency or starter module is present.
- Excel/CSV reader matches the actual file type.
- Generated DDL uses the expected table/column naming rules.
- Table relationship extraction is verified with sample files.
- Import job failure handling records enough context for rerun.

## Do Not

- Do not invent class names or configuration keys without checking the source index.
- Do not replace component extension points with business-local framework code.
- Do not broaden the task into unrelated YSS components unless the user asks.
