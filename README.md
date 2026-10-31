# YSS Skills

用于 CLI 与 Skills 安装、业务规格、产品设计及 Java 后端开发的 27 项公开技能。内容来自 [模板仓](https://github.com/iloveZzz/yss-spec-project-template)，按当前公开清单单向同步；目录不再分发旧前端入口、脚本、测试套件或流程门禁。

## 安装

仅安装技能不需要安装 YSS CLI，也无需创建受管项目。使用 [skills CLI](https://github.com/vercel-labs/skills)，先选择技能和实际 Agent：

```sh
npx skills@latest add iloveZzz/yss-spec-dev-skills --list
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill setup-yss-harness --agent codex
npx skills@latest add iloveZzz/yss-spec-dev-skills --skill yss-validation --agent claude-code
```

默认安装到当前项目；需要跨项目使用时显式加 `--global`。先检查同名技能来源和用户修改，再更新；不自动安装到全部 Agent。需要程序安装或项目接入时，调用 `setup-yss-harness`，按实际 CLI 版本处理。

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
- `skills.sh.json` 对应实际目录；`.yss-export-manifest.json` 记录真实模板提交与导出文件摘要。
- 技能源和宿主副本在模板仓维护，公开仓不反向覆盖模板；历史平台证据通过固定源码链接引用，不作为安装或发布门禁。
- 安装后的宿主发现与 skills.sh 索引更新取决于实际宿主和服务状态；GitHub 同步不代表页面已刷新。

## 许可证

原创内容采用 [MIT License](LICENSE)。保留第三方文件的许可证与声明，参见 [第三方声明](THIRD-PARTY-NOTICES.md)。
