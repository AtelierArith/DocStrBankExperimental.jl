```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

`path`'teki dosyayı okuyun ve bunu `repo`'nun nesne veritabanına gevşek bir blob olarak ekleyin. Ortaya çıkan blob'un [`GitHash`](@ref) değerini döndürün.

# Örnekler

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
