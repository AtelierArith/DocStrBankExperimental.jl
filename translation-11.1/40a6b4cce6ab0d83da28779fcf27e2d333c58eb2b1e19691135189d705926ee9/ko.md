```
iscommit(id::AbstractString, repo::GitRepo) -> Bool
```

커밋 `id` (문자열 형태의 [`GitHash`](@ref))가 저장소에 있는지 확인합니다.

# 예제

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file);

julia> commit_oid = LibGit2.commit(repo, "add test_file");

julia> LibGit2.iscommit(string(commit_oid), repo)
true
```
