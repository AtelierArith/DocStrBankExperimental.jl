```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

Agrega un *push* refspec para el `rmt` especificado. Este refspec contendrá información sobre qué rama(s) empujar.

# Ejemplos

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! nota
    Es posible que necesites [`close`](@ref) y volver a abrir el `GitRemote` en cuestión después de actualizar sus push refspecs para que el cambio tenga efecto y para que las llamadas a [`push`](@ref) funcionen.

