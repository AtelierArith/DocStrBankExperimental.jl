```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

Liest die Datei unter `path` und fügt sie als loses Blob zur Objektdatenbank von `repo` hinzu. Gibt den [`GitHash`](@ref) des resultierenden Blobs zurück.

# Beispiele

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
