```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

Obtiene los refspecs de *fetch* para el `rmt` especificado. Estos refspecs contienen información sobre qué rama(s) obtener.

# Ejemplos

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
