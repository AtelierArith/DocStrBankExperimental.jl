```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

Setzen Sie sowohl die Fetch- als auch die Push-`url` für `remote_name` für das [`GitRepo`](@ref) oder das Git-Repository, das sich im `path` befindet. Typischerweise verwenden Git-Repos `"origin"` als Remote-Namen.

# Beispiele

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```
