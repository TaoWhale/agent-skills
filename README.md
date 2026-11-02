# TaoWhale Agent Skills

可复用的 AI Agent 技能库，适用于 Codex、Claude Code 等支持 Agent Skills 的工具。

**安装一次，之后直接说要做什么。** 写作方式、核对规则和处理步骤已经放进 Skill，不需要每次重新交代。已有上下文直接使用，缺少模板、资料或关键要求时，Agent 再补问。

## 技能目录

| 技能 | 用途 |
| --- | --- |
| [weekly-report](skills/weekly-report/SKILL.md) | 撰写、润色中文周报 |
| [performance-review](skills/performance-review/SKILL.md) | 整理个人绩效考核表，依据实际工作逐项自评 |

## 安装与使用

把下面的话发给 Agent 即可。安装需要当前工具支持技能管理；如需刷新或新开会话，Agent 会提示。

### weekly-report

首次安装：

> 帮我安装 https://github.com/TaoWhale/agent-skills 里的 weekly-report。

以后使用：

> 用 weekly-report 写本周周报。

### performance-review

首次安装：

> 帮我安装 https://github.com/TaoWhale/agent-skills 里的 performance-review。

以后使用：

> 用 performance-review 写本月绩效考核表。

需要时附上模板和工作材料，或告诉 Agent 文件在哪。只有特殊要求才额外说明，不用重复 Skill 中的规则。

## 更新

> 帮我把从 TaoWhale/agent-skills 安装的技能更新到最新版。

安装和更新时，Agent 应检查依赖、保留已有本地修改，并确认技能可用。这些由 Agent 处理，不需要写进每次请求。

<details>
<summary>可选：命令行安装</summary>

需要 Node.js/npm 和 Git，使用 [Skills CLI](https://github.com/vercel-labs/skills)：

```bash
# 查看技能
npx skills add TaoWhale/agent-skills --list

# 将 <skill-name> 换成技能名
npx skills add TaoWhale/agent-skills --skill <skill-name> -g
```

`-g` 表示安装到当前用户范围。可加 `-a codex` 或 `-a claude-code` 指定工具。

</details>

## 资料与权限

Skill 提供处理方法，读取文件、历史会话或外部服务仍取决于当前 Agent 的工具和授权。无法访问的材料可以另行提供；对外发送或发布内容按用户授权执行。

仓库只保存通用方法和虚构示例，不收录真实工作材料、个人评分、客户资料、密钥或个人配置。

## 添加技能

每个技能放在 `skills/<skill-name>/`，提供包含 `name`、`description` 和处理方法的 `SKILL.md`。脚本、参考资料、模板及展示配置按需添加。

新增时更新技能目录和 [CHANGELOG](CHANGELOG.md)，补充一句话安装和使用示例。具体规则放进 Skill，不让用户在提示词里重复。修改通过 Pull Request 审阅。

## 许可证

[MIT](LICENSE)
