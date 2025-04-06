```
fetchheads(repo::GitRepo) -> Vector{FetchHead}
```

`repo`에 대한 모든 fetch head의 목록을 반환하며, 각 fetch head는 이름, URL 및 병합 상태를 포함하는 [`FetchHead`](@ref)로 표현됩니다.

# 예제

```julia-repl
julia> fetch_heads = LibGit2.fetchheads(repo);

julia> fetch_heads[1].name
"refs/heads/master"

julia> fetch_heads[1].ismerge
true

julia> fetch_heads[2].name
"refs/heads/test_branch"

julia> fetch_heads[2].ismerge
false
```
