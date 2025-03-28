```
push_refspecs(rmt::GitRemote) -> Vector{String}
```

Obtenez les *push* refspecs pour le `rmt` spécifié. Ces refspecs contiennent des informations sur quelle(s) branche(s) pousser.

# Exemples

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> close(remote);

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```
