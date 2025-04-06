```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

Belirtilen `rmt` için *fetch* refspec'lerini alır. Bu refspec'ler, hangi dal(lar)ın alınacağına dair bilgi içerir.

# Örnekler

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
