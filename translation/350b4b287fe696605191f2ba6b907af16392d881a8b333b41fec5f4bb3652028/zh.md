```
LibGit2.shortname(ref::GitReference)
```

返回 `ref` 的简短名称，便于“人类阅读”。

```julia-repl
julia> repo = GitRepo(path_to_repo);

julia> branch_ref = LibGit2.head(repo);

julia> LibGit2.name(branch_ref)
"refs/heads/master"

julia> LibGit2.shortname(branch_ref)
"master"
```
