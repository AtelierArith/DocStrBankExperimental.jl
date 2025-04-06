```
add_fetch!(repo::GitRepo, rmt::GitRemote, fetch_spec::String)
```

Ajoute un *fetch* refspec pour le `rmt` spécifié. Ce refspec contiendra des informations sur quelle(s) branche(s) récupérer.

# Exemples

```julia-repl
julia> LibGit2.add_fetch!(repo, remote, "upstream");

julia> LibGit2.fetch_refspecs(remote)
String["+refs/heads/*:refs/remotes/upstream/*"]
```
