```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

Retourne la liste de tous les fetch heads pour `repo`, chacun représenté comme un [`FetchHead`](@ref), y compris leurs noms, URLs et statuts de fusion.

# Exemples

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
