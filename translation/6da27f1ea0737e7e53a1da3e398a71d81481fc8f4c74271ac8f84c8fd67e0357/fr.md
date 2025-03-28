```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

Lit le fichier à `path` et l'ajoute à la base d'objets de `repo` en tant que blob détaché. Retourne le [`GitHash`](@ref) du blob résultant.

# Exemples

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
