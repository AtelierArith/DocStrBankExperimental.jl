```
diff_files(repo::GitRepo, branch1::AbstractString, branch2::AbstractString; kwarg...) -> Vector{AbstractString}
```

显示在 git 仓库 `repo` 中，`branch1` 和 `branch2` 之间发生变化的文件。

关键字参数为：

  * `filter::Set{Consts.DELTA_STATUS}=Set([Consts.DELTA_ADDED, Consts.DELTA_MODIFIED, Consts.DELTA_DELETED]))`，用于设置 diff 的选项。默认情况下显示添加、修改或删除的文件。

仅返回已更改文件的 *名称*，*而不是*其内容。

# 示例

```julia
LibGit2.branch!(repo, "branch/a")
LibGit2.branch!(repo, "branch/b")
# 向 repo 添加一个文件
open(joinpath(LibGit2.path(repo),"file"),"w") do f
    write(f, "hello repo
")
end
LibGit2.add!(repo, "file")
LibGit2.commit(repo, "add file")
# 返回 ["file"]
filt = Set([LibGit2.Consts.DELTA_ADDED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
# 返回 [] 因为现有文件没有被修改
filt = Set([LibGit2.Consts.DELTA_MODIFIED])
files = LibGit2.diff_files(repo, "branch/a", "branch/b", filter=filt)
```

等同于 `git diff --name-only --diff-filter=<filter> <branch1> <branch2>`。
