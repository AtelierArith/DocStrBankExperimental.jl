```
LibGit2.addblob!(repo::GitRepo, path::AbstractString)
```

`path`에 있는 파일을 읽고 이를 `repo`의 객체 데이터베이스에 느슨한 블롭으로 추가합니다. 결과 블롭의 [`GitHash`](@ref)를 반환합니다.

# 예제

```julia
hash_str = string(commit_oid)
blob_file = joinpath(repo_path, ".git", "objects", hash_str[1:2], hash_str[3:end])
id = LibGit2.addblob!(repo, blob_file)
```
