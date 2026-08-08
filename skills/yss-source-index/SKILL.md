---
name: yss-source-index
description: Use when YSS backend component source or frontend UI documentation changes and skill source indexes need refreshing.
---

> **消费项目上下文：** 本公开技能包不携带消费项目的 `AGENTS.md`、`CONTEXT.md` 或 `docs/`。文档中出现的这些路径均指可选的消费项目上下文；技能自身所需的参考资料、资源和脚本已随技能一同提供。

# yss-source-index

Use this maintenance skill to keep YSS skills grounded in current source and documentation.

中文说明：这个技能用于维护 YSS skills 的“源码索引”。后端组件库或前端文档入口变化后，运行脚本刷新引用文件。

## Source Location Policy

- Backend component source is environment-specific. Use `references/source-location.md` before trusting any generated path.
- Preferred explicit setting: `YSS_SOURCE_ROOT=/absolute/path/to/yss-cloud-microservice`.
- Frontend YSS UI components: `the consuming project's optional YSS documentation`
- Frontend YSS UI hooks: `the consuming project's optional YSS documentation`
- Frontend YSS UI skill docs: `the consuming project's optional YSS documentation`

## Refresh Workflow

Run:

```bash
export YSS_SKILLS_ROOT="./path/to/yss-skills"
export YSS_SOURCE_ROOT="./path/to/yss-cloud-microservice"
python3 "$YSS_SKILLS_ROOT/yss-source-index/scripts/refresh-yss-skill-index.py"
```

Backend-only refreshes may set `YSS_REFRESH_FRONTEND=false` to avoid unrelated frontend timestamp churn.

The script updates `references/source-index.md` for backend component skills and `references/frontend-docs.md` for frontend YSS UI skills. Read `references/source-map-config.md` for the full skill-to-source mapping.

中文说明：脚本不会复制大段源码，只会生成可追踪的文档路径、模块路径和关键 Java 入口类，方便 Agent 后续精准读取。

If `YSS_SOURCE_ROOT` is omitted, the script tries to find a repository containing `yss-microservice-components` from the current workspace and common local project folders. If it cannot find one, set `YSS_SOURCE_ROOT` explicitly.

## Output Contract

Generated source indexes should contain:

- source root and generated timestamp
- exact source Git commit and worktree state
- component directories and documentation files
- Maven modules
- key Java classes matched by names such as annotations, auto configurations, properties, aspects, interceptors, handlers, repositories, DTOs, and result objects
- recommended next reads for Agent when performing implementation or troubleshooting

Do not paste full component source into `SKILL.md`. Keep `SKILL.md` short and let specialists read generated indexes or targeted assets only when needed.

## Freshness Gate

Before exact class/config/security guidance, compare the index `Source commit` with `git -C "$YSS_SOURCE_ROOT" rev-parse HEAD`. A mismatch or `dirty` indexed state means `stale`: refresh the index or return `blocked`; do not silently rely on the old snapshot. Historical path hints may still be used only to locate current source.

中文说明：`SKILL.md` 保持短小，细节放到 `references/`，这是为了降低每次触发技能时的上下文成本。

## After Refresh

Validate changed skills with:

```bash
python3 skill-creator/scripts/quick_validate.py $YSS_SKILLS_ROOT/yss-source-index
```
