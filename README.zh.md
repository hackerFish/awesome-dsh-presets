# 🐋 awesome-dsh-presets — DSH 预设与规则合集

**实测可用的 DeepSeek Harness 预设（agent preset）与全局规则（AGENTS.md）精选库。**

> dsh-lab 三件套之三：[dsh-lab](https://github.com/hackerFish/dsh-lab) 实测插件，[awesome-dsh-skills](https://github.com/hackerFish/awesome-dsh-skills) 实测技能，本库实测预设与规则。同一标准：**先验证，再发布**。

## 什么是预设与规则

- **预设（preset）**：一个目录里放一份 `agent.cordis.yml`（插件行列表）与可选 `preset.yml`（显示名/描述）。放入用户预设根目录后，新会话即可选择该预设（机制对照官方 `@deepseek-ai/dsh-agent-presets` 实现）。
- **规则（rules）**：追加到 `~/.dsh/AGENTS.md` 的全局指令片段，对会话内 Agent 持续生效。

## 安装

```bash
git clone https://github.com/hackerFish/awesome-dsh-presets ~/dsh-presets
mkdir -p ~/.dsh/.agent-presets
cp -r ~/dsh-presets/presets/minimal-zh ~/.dsh/.agent-presets/   # 按需挑选
# 规则：
cat ~/dsh-presets/rules/code-quality.md >> ~/.dsh/AGENTS.md     # 按需挑选
```

## 质量保证（禁得起推敲）

- **结构校验**：`node tools/validate-presets.mjs --harness <dsh安装路径>` 全绿——YAML 可解析（含 `!!js` 方言）、顶层为列表、每行含 `id`/`name`、嵌套 group 递归检查。
- **包存在性校验**：预设引用的每个 `@deepseek-ai/*` 包必须在 harness 安装中真实存在。
- **归因透明**：派生预设保留官方版权头并注明"仅改 persona"；原创预设逐行复用官方验证过的行结构并在文件头声明。

## 预设清单

| 预设 | 类型 | 说明 |
|---|---|---|
| [standard-zh](presets/standard-zh/) | 官方派生 | 标准模式全功能 + 中文 persona |
| [minimal-zh](presets/minimal-zh/) | 官方派生 | 极简双工具 + 中文 persona |
| [writer](presets/writer/) | 原创 | 中文写作与文档维护组合 |
| [researcher](presets/researcher/) | 原创 | 信息调研组合 |
| [web-dev](presets/web-dev/) | 原创 | Web 开发工程预制件：23个配套技能，从选型到部署，含设计规则库 |

## 规则清单

| 规则 | 内容 |
|---|---|
| [code-quality](rules/code-quality.md) | 代码质量约定 |
| [commit-discipline](rules/commit-discipline.md) | 提交纪律 |
| [pr-review](rules/pr-review.md) | PR 审查规则 |
| [safety-guardrails](rules/safety-guardrails.md) | 安全护栏 |

## 免责声明

- 派生预设取自官方仓库（MIT），本库的修改透明列明；官方更新后派生版本可能落后，使用前可对照官方源。
- 预设 = 有权执行其插件的组合，请只使用你读过并信任的预设。
- 本库与 DeepSeek 官方无隶属关系。

## 许可证

[MIT](LICENSE)
