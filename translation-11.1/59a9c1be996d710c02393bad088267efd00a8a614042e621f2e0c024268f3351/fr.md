```
LibGit2.isdiff(repo::GitRepo, treeish::AbstractString, pathspecs::AbstractString=""; cached::Bool=false)
```

Vérifie s'il existe des différences entre l'arbre spécifié par `treeish` et les fichiers suivis dans l'arbre de travail (si `cached=false`) ou l'index (si `cached=true`). `pathspecs` sont les spécifications pour les options du diff.

# Exemples

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdiff(repo, "HEAD") # devrait être faux
open(joinpath(repo_path, new_file), "a") do f
    println(f, "voici mon nouveau fichier génial")
end
LibGit2.isdiff(repo, "HEAD") # maintenant vrai
```

Équivalent à `git diff-index <treeish> [-- <pathspecs>]`.
