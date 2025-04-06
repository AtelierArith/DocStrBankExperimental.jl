```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

Clona el repositorio remoto en `repo_url` (que puede ser una URL remota o una ruta en el sistema de archivos local) a `repo_path` (que debe ser una ruta en el sistema de archivos local). Las opciones para la clonación, como si se debe realizar una clonación bare o no, se establecen mediante [`CloneOptions`](@ref).

# Ejemplos

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```
