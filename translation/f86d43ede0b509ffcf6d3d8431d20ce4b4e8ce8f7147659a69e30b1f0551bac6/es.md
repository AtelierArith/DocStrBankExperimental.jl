```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

Obtiene los *push* refspecs para el `rmt` especificado. Estos refspecs contienen información sobre qué rama(s) empujar.

# Ejemplos

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```
