# YSS Spec Dev Skills

[![skills.sh](https://skills.sh/b/iloveZzz/yss-spec-dev-skills)](https://skills.sh/iloveZzz/yss-spec-dev-skills)

面向 AI coding agents 的 YSS 开发技能集合，覆盖产品生命周期、DDD 后端、前端 UI、OpenAPI、数据访问和基础组件。技能源自 [yss-spec-project-template](https://github.com/iloveZzz/yss-spec-project-template) 的公开单向导出。

## 安装

使用 `skills` CLI：

```bash
# 查看可用技能
npx skills add iloveZzz/yss-spec-dev-skills --list

# 安装指定技能
npx skills add iloveZzz/yss-spec-dev-skills --skill yss-validation
npx skills add iloveZzz/yss-spec-dev-skills --skill yss-ui

# 安装全部技能到检测到的 Agent
npx skills add iloveZzz/yss-spec-dev-skills --skill '*' --agent '*' --yes
```

`api-integration` 和 `microapp-commit` 是兼容历史引用的 skill 名称；其余技能通常使用 `yss-*` 名称。安装指定技能时以 `--list` 输出的名称为准。

## 技能范围

- 生命周期与治理：领域建模、YSS Router、OpenAPI Draft、质量与生命周期门禁。
- 后端与基础组件：DDD、Repository、MyBatis、缓存、文件、任务流、日志、安全和数据访问。
- 前端与 UI：YSS UI、Ant Design、Formily、页面模块、Hook 和表格/树高度。
- 工具与微应用：脚手架、数据库元数据生成、Spring Boot 3 升级和微应用提交规范。

技能目录中的 `references/`、`assets/` 和 `scripts/` 是相应技能的支持资料，请在执行技能前按 `SKILL.md` 的要求读取。

## 隐私与安全

`skills` CLI 默认发送匿名使用数据，帮助改进 CLI，并使仓库出现在 skills.sh 的发现页面和使用统计中。可通过以下任一环境变量关闭：

```bash
DISABLE_TELEMETRY=1 npx skills add iloveZzz/yss-spec-dev-skills --skill yss-ui
DO_NOT_TRACK=1 npx skills add iloveZzz/yss-spec-dev-skills --skill yss-ui
```

技能可能包含脚本、代码示例和外部工具调用。安装前请审查对应 `SKILL.md`、`references/`、`assets/`、`scripts/` 和 skills.sh 安全审计结果；审计结果可能延迟，也不是绝对安全保证。不要把本仓库当作可执行代码的可信边界。

## 维护

公开内容由 [yss-spec-project-template](https://github.com/iloveZzz/yss-spec-project-template) 的 `.agents/skills` 单向导出生成。目标仓库不作为技能权威源，也不应直接反向覆盖模板内容。

## 许可证

本仓库原创内容采用 [MIT License](./LICENSE)。Maven Wrapper 等第三方支持文件的声明见 [THIRD-PARTY-NOTICES.md](./THIRD-PARTY-NOTICES.md)；若其他支持文件包含第三方代码、素材或其衍生内容，以该内容附带的许可证或声明为准，无法确认许可时不要发布该文件。
