```
LibGit2.isdirty(repo::GitRepo, pathspecs::AbstractString=""; cached::Bool=false) -> Bool
```

Vérifiez s'il y a eu des modifications dans les fichiers suivis dans l'arbre de travail (si `cached=false`) ou dans l'index (si `cached=true`). `pathspecs` sont les spécifications pour les options du diff.

# Exemples

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.isdirty(repo) # devrait être faux
open(joinpath(repo_path, new_file), "a") do f
    println(f, "voici mon nouveau fichier génial")
end
LibGit2.isdirty(repo) # maintenant vrai
LibGit2.isdirty(repo, new_file) # maintenant vrai
```

Équivalent à `git diff-index HEAD [-- <pathspecs>]`. ```
