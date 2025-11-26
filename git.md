# Git 高级用法学习笔记

这是我们今天学习的所有 Git 命令的总结。

## 1. 基础操作

- `git --version`: 查看 Git 的版本。
- `git status`: 检查当前仓库的状态，查看文件的修改情况。
- `git add <文件名>`: 将文件的修改添加到暂存区。
- `git commit -m "提交信息"`: 将暂存区的修改提交到本地仓库。
- `git commit --amend`: 修改最新一次的提交（可以修改提交信息或增删文件）。
- `git log`: 查看提交历史。
- `git log --oneline`: 以简洁的单行格式查看提交历史。
- `git log --oneline --graph`: 以图形化的方式查看提交历史，能清晰地看到分支和合并。

## 2. 分支 (Branching)

- `git branch`: 列出所有本地分支，并用 `*` 标记当前分支。
- `git branch <新分支名>`: 创建一个新分支。
- `git checkout <分支名>`: 切换到指定的分支。
- `git checkout -b <新分支名>`: 创建一个新分支，并立即切换过去。

## 3. 变基 (Rebasing)

- `git rebase <基础分支>`: 将当前分支的提交“变基”到目标基础分支之上，以创造一个线性的历史。
- `git rebase -i <参考点>`: (交互式变基) 打开一个编辑器，让您可以对一系列提交进行更复杂的操作。
  - **参考点示例**: `HEAD~3` (最近3个提交), `--root` (从根提交开始)。
  - **交互式命令**:
    - `p`, `pick`: 使用该提交。
    - `r`, `reword`: 使用该提交，但修改提交信息。
    - `e`, `edit`: 使用该提交，但暂停以进行修补。
    - `s`, `squash`: 将该提交与前一个提交合并，并合并提交信息。
    - `f`, `fixup`: 将该提交与前一个提交合并，但丢弃该提交的信息。
    - `d`, `drop`: 删除该提交。
- `git rebase --continue`: 在解决冲突后，继续 `rebase` 过程。
- `git rebase --abort`: 完全取消 `rebase` 操作，回到 `rebase` 开始之前的状态。

## 4. 储藏 (Stashing)

- `git stash` 或 `git stash push -m "信息"`: 将未提交的修改（工作区和暂存区）临时保存起来，让工作区变干净。
- `git stash list`: 列出所有储藏。
- `git stash pop`: 应用最近的一个储藏，并从储藏列表中删除它。
- `git stash apply`: 应用最近的一个储藏，但保留它在储藏列表中。

## 5. 引用日志 (Reflog) & 恢复

- `git reflog`: 查看 `HEAD` 引用的所有历史操作记录，是找回“丢失”提交的利器。
- `git reset --hard <哈希值或引用>`: 强制将分支指针和工作区重置到指定的提交状态。常与 `reflog` 配合使用来恢复历史。
