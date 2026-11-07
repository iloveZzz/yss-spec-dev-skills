# YSS Skills

用于 CLI 与 Skills 安装、业务规格、产品设计、Java 后端及 Vue 前端的 **41 项公开技能**。内容从 [模板仓](https://github.com/iloveZzz/yss-spec-project-template) 的共享源单向整理，公开集合与已确认白名单一致。

> 2026-11-07 同步：41 项技能来自 [Template 5.3.2](https://github.com/iloveZzz/yss-spec-project-template/releases/tag/v5.3.2) 的真实提交 [`3df1f846`](https://github.com/iloveZzz/yss-spec-project-template/commit/3df1f846ec68fd4ab3a78d33815025d392c1e9b2)；来源记录与 1362 个文件摘要对应实际分发内容。独立技能与 CLI 内嵌 Bundle 分别更新。

## 选择技能并安装

仅安装技能无需 YSS CLI，也无需初始化受管工程。使用 [skills CLI](https://github.com/vercel-labs/skills) 前，查看实际版本、帮助和 Node 要求；1.7.6 声明 Node `>=22.20.0`，后续版本以实际声明为准。

```sh
npx skills@latest add iloveZzz/yss-spec-dev-skills --list
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill setup-yss-harness --agent codex
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill yss-frontend-application --agent codex
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill yss-validation --agent claude-code
```

默认安装到当前项目，跨项目使用才显式加 `--global`。41 项是可选目录，不要求全部安装，不自动使用 `--all`。同名技能更新前检查原安装来源、实际 Agent、发现路径和用户定制；缺少适用安装工具时，可由 Agent 整理选定技能、必要资源和许可证到宿主支持的技能目录。

技能原有的显式调用限制继续生效。安装不授予生成工程、修改业务源码、提交、推送、部署或向外部发送内容的权限。包内参考和示例不替代消费项目自己的 AGENTS、CONTEXT、DESIGN、规格及接口。

## 程序、技能和工程分别更新

| 路径 | 内容来源 | 更新方式 |
|---|---|---|
| CLI 受管项目 | 当前 Rust 程序内嵌 Bundle 及真实构建记录 | 使用携带所需 Bundle 的程序，再按授权同步明确的项目 |
| 独立技能 | 本公开仓实际分发提交及逐项模板来源 | 按原安装来源和工具实际支持的方式更新选定技能 |
| 应用源码生成 | CLI 内嵌 starter | 只生成新目录；源码、依赖安装与技能接入分别处理 |

本次配套 [CLI 3.3.1](https://github.com/iloveZzz/yss-cli/releases/tag/v3.3.1) 内嵌同源 [Template 5.3.2](https://github.com/iloveZzz/yss-spec-project-template/releases/tag/v5.3.2)。这些版本说明本次发行，不作为未来固定 latest；公开仓更新也不会替换已安装的程序或自动同步消费项目。

Frontend Profile 从 CLI 3.2.0 起支持，安装技能和资料；`scaffold frontend` 从 3.3.0 起支持，仍需对应 Bundle。先读取实际程序的版本和目标命令帮助。旧 Go 安装格式与纯 Rust 不兼容，首次切换按 `setup-yss-harness` 使用新程序和新目录，保留旧安装。

```text
yss version
yss init --help
yss attach --root <已有工程> --profile frontend --installation skills
yss skills list --root <受管目录>
yss scaffold frontend --help
yss scaffold catalog --json
```

CLI 生成源码要求父目录已存在、目标目录不存在，包括已有空目录。生成不安装依赖，也不自动接入技能；需要时才单独 attach。生成收据不授予 sync 管理应用源码的权利。用户级技能目录不运行 `yss init/attach/sync`；同名安装路径先确认所有权，不从一种来源直接覆盖成另一种来源。

## 停止新版分发的旧入口

| 旧入口 | 当前用法 |
|---|---|
| `yss-implementation-contract-compiler` | 实施资格合同和固定证据计划流程取消；明确拆业务票时使用 `to-tickets`，技术设计与实现由实际工程任务承接。业务票不替代实现切片，也不要求安装未公开的内部入口 |
| `yss-openapi-draft-review` | 使用 `yss-openapi-governance` 只读审查；审查请求不自动编辑、导出、冻结或发布 API |
| `yss-prototype-stage` | 产品 UI 使用 `yss-design-system`，业务逻辑/状态原型使用 `prototype`，产物复核使用 `prototype-review`；完整有 UI 的 Spec 需高保真交付，不恢复旧 H1/H2 工具链 |

新版不再携带这三个入口或兼容空技能。消费项目里已安装的旧文件不会因发布新版自动删除，由各项目在明确升级时检查来源、本地定制并处理。`release-yss-cli` 和 `publish-skills-sh` 继续保留为内部维护入口，不在这 41 项公开目录内。

## 技能目录

### 安装与任务协作

用于 CLI、Skills 安装、规格任务整理与技能来源维护。

| 技能 | 用途 |
|---|---|
| [setup-yss-harness](skills/setup-yss-harness/SKILL.md) | 安装或升级 YSS CLI，配置项目或用户级 Skills，初始化、接管、同步项目并处理安装冲突。 |
| [yss-skill-source-index-refresh](skills/yss-skill-source-index-refresh/SKILL.md) | 后端组件源码或前端 YSS UI 文档变化后，刷新技能来源索引并核验平台线、组件摘要与引用。 |

### 后端

用于 YSS Java、DDD、数据访问和服务端契约实现的技能。

| 技能 | 用途 |
|---|---|
| [yss-application](skills/yss-application/SKILL.md) | 实现或排查 YSS 用例编排、事务边界、跨聚合协作、幂等和用例层模型转换。 |
| [yss-ddd-scaffold-generator](skills/yss-ddd-scaffold-generator/SKILL.md) | 直接生成 YSS DDD 多模块后端脚手架，无需需求合同或设计审批。 |
| [yss-domain](skills/yss-domain/SKILL.md) | 在已确认的 DDD 边界内实现或重构领域行为、不变量、状态机与 Gateway；不起草领域设计。 |
| [yss-dto](skills/yss-dto/SKILL.md) | 实现或核验 YSS Result、PageResult、PageQuery、CommandDTO、QueryDTO 及 wire 边界。 |
| [yss-layered-mvc-scaffold-generator](skills/yss-layered-mvc-scaffold-generator/SKILL.md) | 直接生成 YSS 分层 MVC 后端脚手架及参考工程，无需需求合同或设计审批。 |
| [yss-mybatis](skills/yss-mybatis/SKILL.md) | 核验、接入或排查 YSS MyBatis/MyBatis-Plus 的 Mapper/Repository 基类、分页、批量 SQL、扫描与数据源；不生成持久层结构。 |
| [yss-repository](skills/yss-repository/SKILL.md) | 按已确认的 YSS 架构与持久化输入实现或重构 PO、Repository、Convertor、Gateway/Query Adapter；不提供可照抄的业务代码。 |
| [yss-web-controller](skills/yss-web-controller/SKILL.md) | 按当前 API 需求与用例接口实现或重构 YSS Controller、请求 DTO、响应 VO 和 Web Convertor。 |
| [yss-backend-spec-review](skills/yss-backend-spec-review/SKILL.md) | 审查既有 Java 后端的 YSS 规范与需求符合性，并按授权完成整改；普通 PR 审查用 code-review。 |

### Spec 研究、设计与交付

用于研究、业务分析、澄清、完整规格、原型及说明；显式入口遵循原调用政策。

| 技能 | 用途 |
|---|---|
| [yss-product-lifecycle](skills/yss-product-lifecycle/SKILL.md) | 组织 Spec 研究、业务分析、规格与产品原型；在准备将 Spec 或原型交给研发、生成交接提示词或通过 PR/MR 交付材料时使用。 |
| [yss-research](skills/yss-research/SKILL.md) | 调查业务现状、竞品、规则来源、用户资料及技术事实，为需求和方案提供可追溯的证据与限制。 |
| [yss-stage-decision](skills/yss-stage-decision/SKILL.md) | 分析业务目标、场景、范围、规则、责任、权限与状态，比较方案并找出验收缺口；技术设计留给研发。 |
| [grilling](skills/grilling/SKILL.md) | 澄清只有业务方才能决定的问题，检验需求假设和方案取舍；复用已有确认，可调查事实自行核实。 |
| [domain-modeling](skills/domain-modeling/SKILL.md) | 梳理项目的业务词汇、责任范围和关键决策；讨论术语、编辑 CONTEXT.md 或记录 ADR 时使用。 |
| [wayfinder](skills/wayfinder/SKILL.md) | 显式调用时，为跨多个会话的大型工作建立决策地图，逐项澄清未知与依赖。 |
| [to-spec](skills/to-spec/SKILL.md) | 显式将已确认讨论、业务分析和设计综合为完整非技术 Spec，按授权保存或发布。 |
| [yss-design-system](skills/yss-design-system/SKILL.md) | 设计信息结构、流程、内容与视觉，制作产品 UI 原型及交互说明；完整有 UI 的 Spec 交付需高保真原型。 |
| [prototype](skills/prototype/SKILL.md) | 构建可操作的业务逻辑或状态原型，用代表输入验证规则、动作与异常组合；不负责产品视觉方案。 |
| [prototype-review](skills/prototype-review/SKILL.md) | 复核实际产品设计或逻辑原型与规格、验收的一致性，检查承诺行为、适用视觉和可访问性并说明未验证范围。 |
| [to-tickets](skills/to-tickets/SKILL.md) | 仅在明确要求拆票时，按用户行为与验收组织业务 Ticket；不产出技术设计或实现 Slice。 |
| [triage](skills/triage/SKILL.md) | 显式整理需求、反馈和 Issue，核验事实并给出分类、处理建议与简报。 |
| [llm-wiki](skills/llm-wiki/SKILL.md) | Build or refresh a local LLM wiki; use for wiki init, ingest, rebuild, lint, or source-backed wiki questions. |
| [i-have-adhd](skills/i-have-adhd/SKILL.md) | 在研发文档起草、修订、审查报告、PR/MR 描述、复盘和交接表达时，按 YSS 中文规范组织具体、完整的输出，按需图解业务状态、规则与交互；仅作用于当前文档工作。 |
| [handoff](skills/handoff/SKILL.md) | 手动将会话进展和选定产物交接到 GitHub PR 或 GitLab MR。 |

### OpenAPI

用于 YSS API 设计、审查、治理和生成集成的技能。

| 技能 | 用途 |
|---|---|
| [yss-openapi-governance](skills/yss-openapi-governance/SKILL.md) | 审查或维护 YSS OpenAPI 3.1 YAML、接口兼容性，并按需导出 JSON。 |

### 基础组件

用于 YSS 缓存、基础设施、文件、日志和通用组件接入的技能。

| 技能 | 用途 |
|---|---|
| [yss-cache](skills/yss-cache/SKILL.md) | 接入或排查 YSS QueryCache、UpdateCache、ClearCache、TTL、缓存后端与一致性问题。 |
| [yss-distributed-id](skills/yss-distributed-id/SKILL.md) | 接入或排查 YSS 分布式 ID 的 Segment、Snowflake、主键注入与迁移；旧 CosId 只做分诊。 |
| [yss-excel-mvc](skills/yss-excel-mvc/SKILL.md) | 实现或排查 YSS Spring MVC Excel 导入导出、RequestExcel、ResponseExcel 和动态列。 |
| [yss-exception](skills/yss-exception/SKILL.md) | 接入或排查 YSS 统一异常、错误码、异常处理器与 exception starter。 |
| [yss-resilience4j](skills/yss-resilience4j/SKILL.md) | 接入或排查 YSS Resilience4j starter、网关熔断、限流降级与断路器配置。 |
| [yss-security-algorithm](skills/yss-security-algorithm/SKILL.md) | 审查、迁移或排查既有 YSS 加解密、JWT/JWK、密码编码与密钥使用；当前组件禁止新生产接入。 |
| [yss-up-springboot3](skills/yss-up-springboot3/SKILL.md) | 审查或迁移 YSS Spring Boot 2 到 3 的依赖、Jakarta 与 Spring Cloud 兼容性。 |
| [yss-userinfo](skills/yss-userinfo/SKILL.md) | 接入或排查 YSS CurrentUserProvider、已认证 SecurityContext、受信网关头适配与后台用户上下文。 |
| [yss-validation](skills/yss-validation/SKILL.md) | 接入或排查 YSS Bean Validation、校验消息与校验错误映射。 |

### 审计日志

用于应用审计日志的接入与排查。

| 技能 | 用途 |
|---|---|
| [yss-audit-log](skills/yss-audit-log/SKILL.md) | 接入或排查 YSS AuditLog 的 SpEL 摘要、异步发布、订阅注册与审计投递。 |

### Vue 前端工程与原型逻辑

用于 Vue 应用工程、设计还原，以及状态、数据流、生命周期与 composable 方法。

| 技能 | 用途 |
|---|---|
| [yss-frontend-application](skills/yss-frontend-application/SKILL.md) | Use when implementing, engineering, or reviewing Vue 3 frontend applications from high-fidelity designs, prototypes, page code, or OpenAPI contracts（前端工程化、设计还原、接口生成与工程审查）；纯产品设计或原型改稿使用 yss-design-system。 |
| [vue-best-practices](skills/vue-best-practices/SKILL.md) | Use when implementing or reviewing Vue 3 reactivity, component data flow, composables, or Vue-specific runtime behavior. Prefer Composition API with script setup and TypeScript within the project's conventions. Pure copy, color, or spacing edits do not trigger this skill. |
| [create-adaptable-composable](skills/create-adaptable-composable/SKILL.md) | Create a library-grade Vue composable that accepts maybe-reactive inputs (MaybeRef / MaybeRefOrGetter) so callers can pass a plain value, ref, or getter. Normalize inputs with toValue()/toRef() inside reactive effects (watch/watchEffect) to keep behavior predictable and reactive. Use this skill when user asks for creating adaptable or reusable composables. |
| [yss-frontend-scaffold-generator](skills/yss-frontend-scaffold-generator/SKILL.md) | 在不存在的新目录生成 YSS Vue 3 最小前端工程；需要新建应用脚手架时使用，已有工程改造、只读 review 或仅安装技能不触发生成。 |

## 包内资源与来源

- 每项技能保留必要的正文、方法、静态资产、已有运行时元数据和许可证；跨技能方法按包投影到 `references/shared/`，供单项安装读取，不创建额外技能入口。
- 资源投影来自同一共享源，包内相对路径会因独立分发改写。ShowMe 方法及许可保持源内容；有意标为缺陷的教学例子保留其缺失路径，不作为实际运行资源。
- `skills.sh.json` 对应上述 41 项及七个分组。`.yss-export-manifest.json` 记录同一真实模板提交、41 项逐项来源及 1362 个最终文件的 SHA-256；模板源与公开分发提交分别记录，不用本地源提交冒称远端已发布。
- 模板源提交、公开分发提交和文件摘要分别说明。独立技能更新不会替换 CLI，受管项目也不会自动读取模板 main。
- 原始引入信息保留在技能的 `upstream.json`、包内来源说明与许可中；共享技能适配历史见 [Matt 来源说明](https://github.com/iloveZzz/yss-spec-project-template/blob/9887d0d9915a9edcf9679dca16a236cef0fd5efa/.template-spec/agents/matt-skills-adaptation.md) 和 [Frontend 来源说明](https://github.com/iloveZzz/yss-spec-project-template/blob/9887d0d9915a9edcf9679dca16a236cef0fd5efa/.template-spec/agents/frontend-skills-adaptation.md)。这些历史资料不构成安装或发布资格。
- 结构核对不能证明宿主已加载、安装运行成功、Windows 原生验证或 skills.sh 收录。仅在实际观察后报告相应结果，不自动轮询收录或改变遥测设置。

## 许可证

原创 YSS 内容采用 [MIT License](LICENSE)。第三方材料保留其实际许可证、版权和来源；包括包内重复投影时的对应声明，见 [第三方声明](THIRD-PARTY-NOTICES.md)。
