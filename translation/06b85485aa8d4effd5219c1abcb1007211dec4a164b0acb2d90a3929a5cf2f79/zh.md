```
checkout!(repo::GitRepo, commit::AbstractString=""; force::Bool=true)
```

相当于 `git checkout [-f] --detach <commit>`。在 `repo` 中检出 git 提交 `commit`（以字符串形式表示的 [`GitHash`](@ref)）。如果 `force` 为 `true`，则强制检出并丢弃任何当前更改。请注意，这会分离当前的 HEAD。

# 示例

```julia
repo = LibGit2.GitRepo(repo_path)
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "111
")
end
LibGit2.add!(repo, "file1")
commit_oid = LibGit2.commit(repo, "add file1")
open(joinpath(LibGit2.path(repo), "file1"), "w") do f
    write(f, "112
")
end
# 如果没有 force=true，这将失败
# 因为文件有修改
LibGit2.checkout!(repo, string(commit_oid), force=true)
```
