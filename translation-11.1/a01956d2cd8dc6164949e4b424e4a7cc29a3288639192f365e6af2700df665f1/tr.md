```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

`repo` için tüm fetch head'lerin listesini döndürür, her biri [`FetchHead`](@ref) olarak temsil edilir ve adları, URL'leri ve birleştirme durumları dahil edilir.

# Örnekler

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
