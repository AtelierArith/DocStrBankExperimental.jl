```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

读取 `path` 处的文件，并将其作为松散的 blob 添加到 `repo` 的对象数据库中。返回结果 blob 的 [`GitHash`](@ref)。

# 示例

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
