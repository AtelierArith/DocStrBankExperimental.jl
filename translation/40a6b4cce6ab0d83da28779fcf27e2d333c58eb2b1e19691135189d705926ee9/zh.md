```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

检查提交 `id`（它是字符串形式的 [`GitHash`](@ref)）是否在该仓库中。

# 示例

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "add test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
