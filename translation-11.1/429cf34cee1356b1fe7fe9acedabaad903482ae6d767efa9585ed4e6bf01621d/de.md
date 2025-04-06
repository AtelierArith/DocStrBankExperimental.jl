```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

Holen Sie sich die *fetch* refspecs für das angegebene `rmt`. Diese refspecs enthalten Informationen darüber, von welchem Branch(es) abgerufen werden soll.

# Beispiele

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
