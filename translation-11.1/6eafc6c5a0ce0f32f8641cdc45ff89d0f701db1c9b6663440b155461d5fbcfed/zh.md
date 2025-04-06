```
reset!(repo::GitRepo, id::GitHash, mode::Cint=Consts.RESET_MIXED)
```

将仓库 `repo` 重置为 `id` 的状态，使用 `mode` 设置的三种模式之一：

1. `Consts.RESET_SOFT` - 将 HEAD 移动到 `id`。
2. `Consts.RESET_MIXED` - 默认，将 HEAD 移动到 `id` 并将索引重置为 `id`。
3. `Consts.RESET_HARD` - 将 HEAD 移动到 `id`，将索引重置为 `id`，并丢弃所有工作更改。

# 示例

```julia
# 获取更改
LibGit2.fetch(repo)
isfile(joinpath(repo_path, our_file)) # 将为 false

# 快进合并更改
LibGit2.merge!(repo, fastforward=true)

# 因为本地没有任何文件，但远程有
# 一个文件，我们需要重置分支
head_oid = LibGit2.head_oid(repo)
new_head = LibGit2.reset!(repo, head_oid, LibGit2.Consts.RESET_HARD)
```

在这个例子中，从中获取的远程确实在其索引中有一个名为 `our_file` 的文件，这就是我们必须重置的原因。

等同于 `git reset [--soft | --mixed | --hard] <id>`。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
head_oid = LibGit2.head_oid(repo)
open(joinpath(repo_path, "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
mode = LibGit2.Consts.RESET_HARD
# 将丢弃对 file1 的更改
# 并取消暂存
new_head = LibGit2.reset!(repo, head_oid, mode)
```
