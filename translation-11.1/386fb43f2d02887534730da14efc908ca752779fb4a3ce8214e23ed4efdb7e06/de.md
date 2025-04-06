```
clone(repo_url::AbstractString, repo_path::AbstractString, clone_opts::CloneOptions)
```

Klonen Sie das Remote-Repository unter `repo_url` (das eine Remote-URL oder einen Pfad im lokalen Dateisystem sein kann) nach `repo_path` (das ein Pfad im lokalen Dateisystem sein muss). Optionen für den Klon, wie z.B. ob ein Bare-Klon durchgeführt werden soll oder nicht, werden durch [`CloneOptions`](@ref) festgelegt.

# Beispiele

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo = LibGit2.clone(repo_url, "/home/me/projects/Example")
```
