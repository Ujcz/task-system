# 01 TAPD 需求读取与澄清

## 目标

把 TAPD 原始需求、评论、父子单关系和历史上下文整理成可以开发、可以测试、可以交付的上下文。

## 输入

- TAPD 链接或 ID。
- 类型：需求、缺陷、任务。
- 所属项目：Hotchat、Tikko 或其他。
- 用户补充的业务背景。
- 已知分支、PR、提交或历史文档。

## 必做动作

1. 定位 TAPD 单据类型和完整 ID。
2. 读取标题、正文、状态、负责人、创建人、评论、父子关系。
3. 区分主单和子单：主单承载总体说明，子单承载开发状态。
4. 提取验收标准，不足时列为待确认项。
5. 判断是否需要 Wiki 或本地交付文档。
6. 不直接覆盖 TAPD 正文，除非用户明确要求。

## 输出：Context Pack

```text
Context Pack
- tapd_target:
- type:
- title:
- current_status:
- owner:
- parent_or_children:
- objective:
- original_description_summary:
- key_comments:
- acceptance:
- non_goals:
- open_questions:
- initial_repo_guess:
```

## 读者视角

- 给自己：明确这次到底要做什么。
- 给测试：提炼可验证点。
- 给产品：保留业务目标和不涉及范围。
- 给部署：提前识别配置、SQL、MQ、定时任务和发布依赖。

## 阶段出口

满足以下条件才能进入分析设计：

- 已确认 TAPD 类型和目标单据。
- 已提取目标、范围和验收标准。
- 已列出待确认问题。
- 已初步判断涉及仓库和风险类型。

