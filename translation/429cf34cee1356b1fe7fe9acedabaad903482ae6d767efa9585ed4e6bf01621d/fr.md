```
fetch_refspecs(rmt::GitRemote) -> Vector{String}
```

Obtenez les *fetch* refspecs pour le `rmt` spécifié. Ces refspecs contiennent des informations sur quelle(s) branche(s) récupérer.

# Exemples

```julia-repl
julia> remote = LibGit2.get(LibGit2.GitRemote, repo, "upstream");

julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
