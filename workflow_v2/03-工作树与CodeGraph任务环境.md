# 03 Worktree 与 CodeGraph 任务环境

## 目标

保证并行任务之间隔离，避免在 `D:\jcz\source` 主干目录里直接开发，也避免使用错误的 CodeGraph 视角分析任务分支。

## 主目录职责

`D:\jcz\source` 保持 `master` 或主干基线，用于：

- 同步主干。
- 创建任务 worktree。
- 做主干现状分析。
- 作为长期 CodeGraph 基线索引。

## 任务目录职责

`D:\jcz\worktrees\<task-dir>` 用于：

- 当前任务分支开发。
- 多仓同分支联动。
- 当前任务级 CodeGraph 分析。
- Review、验证、交付前检查。

## 创建 worktree

使用 `kissu-multi-repo-worktree` 脚本，不手写零散命令。

```powershell
powershell -ExecutionPolicy Bypass -File "C:\Users\QH\.codex\skills\kissu-multi-repo-worktree\scripts\new-worktree.ps1" -Branch "feature/rank/score_opt" -Repos "core","kissu-server-rank"
```

## 初始化任务 CodeGraph

```powershell
codegraph init -i D:\jcz\worktrees\feature-rank-score_opt
codegraph status D:\jcz\worktrees\feature-rank-score_opt
```

## 使用规则

- 主干问题使用 `D:\jcz\source` 索引。
- 当前任务问题使用 `D:\jcz\worktrees\<task-dir>` 索引。
- 不要把 `D:\jcz` 整体作为 CodeGraph 索引根目录。
- 任务涉及多个仓库时，把所有相关仓库放进同一个任务目录。

## 阶段检查

实现前必须确认：

- 当前路径在 `D:\jcz\worktrees\<task-dir>\<repo>`。
- 当前分支不是 `master`。
- 多仓任务使用同一个分支名。
- CodeGraph 指向任务目录而不是主干目录。

