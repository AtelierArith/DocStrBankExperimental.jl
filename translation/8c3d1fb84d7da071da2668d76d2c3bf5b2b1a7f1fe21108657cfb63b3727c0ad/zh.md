```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

尝试对当前分支进行自动合并变基，如果提供了 `upstream`，则从其进行变基，否则从上游跟踪分支进行变基。`newbase` 是要变基到的分支。默认情况下，这是 `upstream`。

如果出现无法自动解决的冲突，变基将中止，保留仓库和工作树的原始状态，并且该函数将抛出 `GitError`。这大致相当于以下命令行语句：

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```
