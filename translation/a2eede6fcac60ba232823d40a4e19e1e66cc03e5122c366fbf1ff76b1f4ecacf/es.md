```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

Agrega un *fetch* refspec para el `rmt` especificado. Este refspec contendrá información sobre qué rama(s) obtener.

# Ejemplos

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
