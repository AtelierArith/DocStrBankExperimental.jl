```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

Devuelve la lista de todos los fetch heads para `repo`, cada uno representado como un [`FetchHead`](@ref), incluyendo sus nombres, URLs y estados de fusión.

# Ejemplos

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
