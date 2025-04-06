```
is_ancestor_of(a::AbstractString, b::AbstractString, repo::GitRepo) -> Bool
```

`a`가 `b`의 조상인 경우 `true`를 반환합니다. 여기서 `a`는 문자열 형태의 [`GitHash`](@ref)이고, `b`는 문자열 형태의 [`GitHash`](@ref)입니다.

# 예제

```julia-repl
julia> repo = GitRepo(repo_path);

julia> LibGit2.add!(repo, test_file1);

julia> commit_oid1 = LibGit2.commit(repo, "commit1");

julia> LibGit2.add!(repo, test_file2);

julia> commit_oid2 = LibGit2.commit(repo, "commit2");

julia> LibGit2.is_ancestor_of(string(commit_oid1), string(commit_oid2), repo)
true
```
