```
name(rmt::GitRemote)
```

Holen Sie sich den Namen eines Remote-Repositorys, zum Beispiel `"origin"`. Wenn das Remote anonym ist (siehe [`GitRemoteAnon`](@ref)), ist der Name eine leere Zeichenfolge `""`.

# Beispiele

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```
