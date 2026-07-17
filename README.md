# review-x-content

一个用于发布前审核 X（原 Twitter）内容的 Codex Skill。它会分别检查：

1. 草稿是否可能违反 X 平台规则；
2. 草稿是否符合 X 创作者变现和 Creator Revenue Sharing 要求；
3. 哪些内容需要删除、改写、补充来源或添加敏感媒体/AI 披露标签。

> 本 Skill 提供风险评估和修改建议，不代表 X 的正式裁定，也不构成法律意见。

## 功能

- 审核推文、长文、帖子串、标题、图片说明和视频文案；
- 将“能否发布”与“能否变现”分开判断；
- 识别暴力、仇恨、骚扰、隐私、成人内容、非法商品、垃圾信息、平台操纵、合成媒体和知识产权等风险；
- 检查创作者收益中的禁止内容、受限内容和账号资格待确认项；
- 给出风险等级、逐项依据、最小改动版文案和发布前操作清单；
- 审核时优先核对 X 最新官方政策，避免依赖过时规则。

## 安装

将仓库克隆或下载到 Codex 的 Skills 目录：

```bash
git clone https://github.com/blueskylh/review-x-content.git ~/.codex/skills/review-x-content
```

重新启动 Codex，或开始一个新任务，让 Skill 被重新发现。

## 使用方法

在 Codex 中显式调用：

```text
使用 $review-x-content 审核下面这条准备发布到 X 的推文，检查平台违规风险和创作者收益风险，并给出最小改动版：

[在这里粘贴草稿]
```

审核帖子串时，请提供完整顺序：

```text
使用 $review-x-content 审核这个 X 帖子串。我的账号参加 Creator Revenue Sharing，目标受众是美国英语用户：

1/ ...
2/ ...
3/ ...
```

如果内容带有图片或视频，请同时附上媒体，或描述其中的关键画面，并说明它是否由 AI 生成。

## 输出内容

Skill 默认返回：

- X 平台规则结论；
- 创作者变现结论；
- 置信度；
- 风险片段、政策类别、原因和修改建议；
- 尽量保留原意的完整修改稿；
- 媒体标签、AI 披露、来源及账号资格等待确认项；
- 本次核验过的 X 官方政策链接和日期。

## 判断说明

X 允许发布的内容不一定符合变现或推荐要求。例如，部分正确标注的成人、暴力或敏感内容可能允许留在平台，但仍可能受到变现限制。因此，本 Skill 始终给出两套独立结论。

账号年龄、地区、订阅状态、粉丝数、展示量、Stripe、身份验证和历史违规等资格，无法仅凭一篇草稿确定。缺少相关信息时，Skill 会将其列为“待确认”，而不是猜测。

## 政策来源

主要核对以下 X 官方页面：

- [The X Rules](https://help.x.com/en/rules-and-policies/x-rules)
- [X’s Creator Monetization Standards](https://help.x.com/en/rules-and-policies/content-monetization-standards)
- [Creator Revenue Sharing](https://help.x.com/en/using-x/creator-revenue-sharing)
- [X Rules and policies](https://help.x.com/en/rules-and-policies)

详细来源清单位于 [`references/policy-sources.md`](references/policy-sources.md)。X 可能随时更新政策，实际审核时应重新访问官方页面。

## 仓库结构

```text
review-x-content/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    └── policy-sources.md
```

## 许可证

本仓库目前未附带开源许可证。除非仓库所有者另行授权，默认保留所有权利。

