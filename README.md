# YSS Skills

用于 CLI 与 Skills 安装、业务规格、产品设计及 Java 后端开发的 27 项公开技能。内容来自 [模板仓](https://github.com/iloveZzz/yss-spec-project-template)，按当前公开清单单向同步；目录不再分发旧前端入口、脚本、测试套件或流程门禁。

## 安装

仅安装技能不需要安装 YSS CLI，也无需创建受管项目。使用 [skills CLI](https://github.com/vercel-labs/skills)，先选择技能和实际 Agent：

```sh
npx skills@latest add iloveZzz/yss-spec-dev-skills --list
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill setup-yss-harness yss-design-system --agent codex
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill yss-validation --agent claude-code
```

默认安装到当前项目；需要跨项目使用时显式加 `--global`。先检查同名技能来源和用户修改，再更新；不自动安装到全部 Agent。需要程序安装或项目接入时，调用 `setup-yss-harness`，按实际 CLI 版本处理。

## 本次同步：安装与产品设计

2026-11-01 对齐 [Template v5.0.5](https://github.com/iloveZzz/yss-spec-project-template/releases/tag/v5.0.5) 与 [CLI v3.0.5](https://github.com/iloveZzz/yss-cli/releases/tag/v3.0.5)，并包含后续组件许可说明修正。

| 技能 | 当前能力 |
|---|---|
| [setup-yss-harness](skills/setup-yss-harness/SKILL.md) | 默认从 GitHub 获取正式 CLI，按实际版本区分程序升级、项目技能、用户级技能与工程同步；支持显式 GitLab 次级来源 |
| [yss-design-system](skills/yss-design-system/SKILL.md) | 产品设计、Vue + shadcn-vue 草稿与可操作原型、交互说明、状态/规则图解；包内附带组件快照、示例 Token、必要研究/复核参考及许可 |

这两个技能可分别独立安装，无需补装整个模板或其他技能。设计资产只用于新的原型目录；项目规范和用户确认的业务规则仍是输入，示例不自动成为项目事实。

本轮仅同步上述两项，其余 25 项保持既有版本。选定技能来源固定为模板提交 [`624b7a7a`](https://github.com/iloveZzz/yss-spec-project-template/commit/624b7a7aed030e72761b6123919bad70862d14da)，不把部分同步描述为全库更新。技能实际调用时仍核对最新正式 CLI 与目标平台资产，不把本次版本记录写死为未来安装目标。

## 项目受管技能

YSS CLI 3.0.1 起提供精简接口：`project` 安装技能与必要项目文档，`skills` 安装技能、宿主入口及必要引用资源，两者都不附带治理门禁。

```sh
yss init --root ./demo --profile spec --installation skills
yss skills list --root ./demo
yss skills ensure setup-yss-harness yss-validation --root ./demo
yss sync --root ./demo --dry-run
```

受管项目使用 CLI 内嵌 Bundle；独立安装使用本公开仓，二者来源和更新方式不同。用户级技能目录不应执行 `yss init/attach/sync`。旧 CLI、插件与 `plan/apply` 流程不兼容新接口，首次切换由 Agent 下载正式发行包并使用新程序安装。

## 内容与来源

- `skills/` 保存公开技能、引用和资产；每项必要的模板资料与跨技能引用资源放在该技能内。
- `skills.sh.json` 对应实际目录；`.yss-export-manifest.json` 记录模板来源与导出文件摘要；技能条目的 `source_commit` 优先于顶层完整同步的历史 `source.commit`，用于追踪部分更新。
- 技能源和宿主副本在模板仓维护，公开仓不反向覆盖模板；历史平台证据通过固定源码链接引用，不作为安装或发布门禁。
- 安装后的宿主发现与 skills.sh 索引更新取决于实际宿主和服务状态；GitHub 同步不代表页面已刷新。

## 许可证

原创内容采用 [MIT License](LICENSE)。保留第三方文件的许可证与声明，参见 [第三方声明](THIRD-PARTY-NOTICES.md)。
