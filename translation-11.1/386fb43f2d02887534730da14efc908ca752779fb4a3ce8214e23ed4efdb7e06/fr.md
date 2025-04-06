```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

Clone le dépôt distant à `repo_url` (qui peut être une URL distante ou un chemin sur le système de fichiers local) vers `repo_path` (qui doit être un chemin sur le système de fichiers local). Les options pour le clonage, telles que la possibilité d'effectuer un clonage nu ou non, sont définies par [`CloneOptions`](@ref).

# Exemples

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```
