```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

Belirtilen `rmt` için *push* refspec'lerini alır. Bu refspec'ler hangi dal(lar)ın itileceği hakkında bilgi içerir.

# Örnekler

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```
