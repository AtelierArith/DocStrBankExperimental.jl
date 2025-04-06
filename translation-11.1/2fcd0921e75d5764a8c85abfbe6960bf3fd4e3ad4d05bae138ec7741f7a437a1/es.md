```
name(rmt::GitRemote)
```

Obtiene el nombre de un repositorio remoto, por ejemplo `"origin"`. Si el remoto es anónimo (ver [`GitRemoteAnon`](@ref)), el nombre será una cadena vacía `""`.

# Ejemplos

```julia-repl
julia> repo_url = "https://github.com/JuliaLang/Example.jl";

julia> repo = LibGit2.clone(cache_repo, "test_directory");

julia> remote = LibGit2.GitRemote(repo, "origin", repo_url);

julia> name(remote)
"origin"
```
