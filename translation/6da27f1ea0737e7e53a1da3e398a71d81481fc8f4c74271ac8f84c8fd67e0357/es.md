```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

Lee el archivo en `path` y lo agrega a la base de datos de objetos de `repo` como un blob suelto. Devuelve el [`GitHash`](@ref) del blob resultante.

# Ejemplos

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
