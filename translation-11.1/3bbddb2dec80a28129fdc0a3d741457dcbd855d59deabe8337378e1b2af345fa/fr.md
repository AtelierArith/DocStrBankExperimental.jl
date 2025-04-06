```
set_remote_url(repo::GitRepo, remote_name, url)
set_remote_url(repo::String, remote_name, url)
```

Définir à la fois l'`url` de récupération et de poussée pour `remote_name` pour le [`GitRepo`](@ref) ou le dépôt git situé à `path`. En général, les dépôts git utilisent `"origin"` comme nom distant.

# Exemples

```julia
repo_path = joinpath(tempdir(), "Example")
repo = LibGit2.init(repo_path)
LibGit2.set_remote_url(repo, "upstream", "https://github.com/JuliaLang/Example.jl")
LibGit2.set_remote_url(repo_path, "upstream2", "https://github.com/JuliaLang/Example2.jl")
```
