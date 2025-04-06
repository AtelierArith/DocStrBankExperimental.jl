```
name(rmt::GitRemote)
```

Obtenez le nom d'un dépôt distant, par exemple `"origin"`. Si le dépôt distant est anonyme (voir [`GitRemoteAnon`](@ref)), le nom sera une chaîne vide `""`.

# Exemples

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```
