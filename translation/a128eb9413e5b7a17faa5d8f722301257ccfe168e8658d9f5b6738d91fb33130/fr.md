```
add_push!(repo::GitRepo, rmt::GitRemote, push_spec::String)
```

Ajoute un *push* refspec pour le `rmt` spécifié. Ce refspec contiendra des informations sur quelle(s) branche(s) pousser.

# Exemples

```julia-repl
julia> LibGit2.add_push!(repo, remote, "refs/heads/master");

julia> remote = LibGit2.get(LibGit2.GitRemote, repo, branch);

julia> LibGit2.push_refspecs(remote)
String["refs/heads/master"]
```

!!! note
    Vous devrez peut-être [`close`](@ref) et rouvrir le `GitRemote` en question après avoir mis à jour ses push refspecs afin que le changement prenne effet et que les appels à [`push`](@ref) fonctionnent.

