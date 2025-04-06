```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

在 `repo` 仓库中检出一个新的 git 分支。`commit` 是 [`GitHash`](@ref)，以字符串形式表示，将作为新分支的起点。如果 `commit` 是空字符串，将使用当前的 HEAD。

关键字参数包括：

  * `track::AbstractString=""`：此新分支应跟踪的远程分支的名称（如果有）。如果为空（默认值），则不会跟踪任何远程分支。
  * `force::Bool=false`：如果为 `true`，则强制创建分支。
  * `set_head::Bool=true`：如果为 `true`，则在分支创建完成后，将分支头设置为 `repo` 的 HEAD。

等效于 `git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]`。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```
