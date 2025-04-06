```
name(rmt::GitRemote)
```

获取远程仓库的名称，例如 `"origin"`。如果远程是匿名的（见 [`GitRemoteAnon`](@ref)），名称将是一个空字符串 `""`。

# 示例

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```
