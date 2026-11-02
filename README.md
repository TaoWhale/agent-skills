# TaoWhale Agent Skills

可复用的 AI Agent 技能库，面向 Codex、Claude Code 等支持 Agent Skills 的工具。一个仓库维护多个技能，每个技能独立安装，按需使用。

## 当前技能

| 技能 | 用途 | 说明 |
| --- | --- | --- |
| [weekly-report](skills/weekly-report/SKILL.md) | 中文周报撰写与润色 | 根据工作材料核对归属和进度，按项目归纳，不编造计划和感想 |
| [performance-review](skills/performance-review/SKILL.md) | 个人绩效考核表撰写与自评 | 按模板整理工作指标和评分标准，逐项依据事实评分，最后汇总，不预设总分 |

## 安装：让 Agent 帮你完成

已经在使用有本地文件和命令执行能力的 Codex、Claude Code 等工具，可以把下面这段话发给它：

> 请从 https://github.com/TaoWhale/agent-skills 安装 weekly-report 技能，供当前 Agent 在各项目中使用。请先查看 README 和技能内容、检查所需环境；如果已有同名技能且存在本地修改，请保留修改，不直接覆盖。

安装完成后，重新打开会话或按当前工具的方式刷新技能。请 Agent 确认能找到 `weekly-report`。

## 安装：使用通用命令

电脑需要可用的 Node.js/npm 和 Git。使用开源的 [Skills CLI](https://github.com/vercel-labs/skills) 安装，不需要克隆仓库，也不需要为这个公开仓库申请访问权限。

安装周报技能，交互选择要使用的 Agent：

```bash
npx skills add TaoWhale/agent-skills --skill weekly-report -g
```

也可以指定目标工具，只运行需要的一条：

```bash
# Codex
npx skills add TaoWhale/agent-skills --skill weekly-report -g -a codex

# Claude Code
npx skills add TaoWhale/agent-skills --skill weekly-report -g -a claude-code
```

`-g` 表示安装到当前用户范围，可在不同项目中使用。安装器可能提示选择链接或复制方式，按环境选择即可。

查看仓库中的所有技能：

```bash
npx skills add TaoWhale/agent-skills --list
```

后续加入其他技能时，将 `--skill weekly-report` 换成对应名称即可；不需要为每个技能新建仓库。

## 使用周报技能

在安装技能的 Agent 中直接提出需求，例如：

> 使用 weekly-report，整理我本周的个人周报。以下是本周工作记录和已确认的下周安排：……

需要结合本地历史会话时，明确日期、项目和来源范围，例如：

> 使用 weekly-report，结合本周“示例项目”在 Codex、Claude Code 中可访问的相关会话和我提供的工作记录整理周报。请核对本人负责与配合事项，区分完成、推进中和计划。

以上项目名称仅为虚构示例。日期默认按使用者时区理解，也可以直接提供起止日期。

- 默认以“本周工作总结”为主体，可保留“下周工作计划”和“需要协助、思考、总结、学习成长”。
- 后两部分有依据才写，不编造任务、截止日期、协作诉求或感想。
- 没有相关事项时可写“暂无”；缺少材料或安排尚不明确时可写“待补充”；也可以要求省略空栏目。
- 有公司模板时直接提供，以用户模板为准。
- 仅生成和整理内容，不自动发送周报。

## 使用绩效考核技能

安装方式与周报技能相同，将技能名替换为 `performance-review`：

```bash
npx skills add TaoWhale/agent-skills --skill performance-review -g
```

例如：

> 使用 performance-review，按我提供的模板和本月工作记录整理个人考核表。重点写好工作指标与评分标准，逐项给出自评分依据，最后汇总总分；没有必要内容时备注留空。

- 先核对本人负责、协作事项和实际状态，再对照各项标准评分。
- 不按提交数量、投入时间或预设总分倒推分数；不编造收益和超额完成情况。
- 缺少决定性证据时留空或说明待补充，不把缺资料当作零分。
- 保留公司已有制度、模板和用户修改；主管评分及签字不代填。
- 可配合 weekly-report 核对资料，也可单独使用。生成 Excel 等文件需要运行环境具备相应的文件编辑能力。

## 能力与资料范围

这个仓库提供写作规则，**不包含专用的 Codex / Claude Code 会话采集脚本**。能否读取某个工具的历史，取决于运行环境提供的会话接口、本地文件权限和日志格式。Agent 应按授权范围只读访问、先筛选项目和日期；无法读取时说明缺口，使用当前材料或用户提供的导出文件。

只在浏览器聊天中使用时，可以提供工作记录或导出文件，但不能仅靠安装技能自动获得电脑上的其他 Agent 会话。技能本身不绑定模型服务；资料处理仍遵循所用 Agent 及模型服务的数据政策。

仓库只保存通用方法和虚构示例。请勿提交真实周报、考核表、个人评分、原始会话、客户资料、密钥或个人配置。

## 更新

请先备份自己对技能的修改，再执行：

```bash
npx skills update weekly-report -g
```

需要图形界面管理多个 Agent 的技能，可自行选择兼容的技能管理器；它不是本仓库的必需依赖。

## 添加新技能

```text
skills/
├── weekly-report/
│   ├── SKILL.md
│   └── agents/openai.yaml
└── performance-review/
    ├── SKILL.md
    └── agents/openai.yaml
```

新技能使用独立目录，`SKILL.md` 顶部提供 `name` 和 `description`。根据实际需要添加 `references/`、`scripts/` 或 `assets/`，更新上面的技能表和 CHANGELOG。修改通过 Pull Request 审阅，避免把个人配置或真实工作资料写进通用规则。

## 许可证

[MIT](LICENSE)
