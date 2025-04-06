```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

Gibt die Liste aller Fetch-Head für `repo` zurück, wobei jeder als [`FetchHead`](@ref) dargestellt wird, einschließlich ihrer Namen, URLs und Merge-Status.

# Beispiele

```julia-repl
julia> fetch_heads = LibGit2.fetchheads(repo);

julia> fetch_heads[1].name
"refs/heads/master"

julia> fetch_heads[1].ismerge
true

julia> fetch_heads[2].name
"refs/heads/test_branch"

julia> fetch_heads[2].ismerge
false
```
