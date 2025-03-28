```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

Holen Sie sich die *push* refspecs für das angegebene `rmt`. Diese refspecs enthalten Informationen darüber, welche(n) Branch(es) gepusht werden sollen.

# Beispiele

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```
