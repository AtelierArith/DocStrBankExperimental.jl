```
GitRevWalker(repo::GitRepo)
```

`GitRevWalker`는 git 저장소 `repo`의 *수정* (즉, 커밋)을 *탐색*합니다. 이는 저장소의 커밋 모음이며, 반복(iteration) 및 [`LibGit2.map`](@ref)과 [`LibGit2.count`](@ref) 호출을 지원합니다 (예를 들어, `LibGit2.count`는 저장소의 커밋 중 특정 저자가 만든 커밋의 비율을 결정하는 데 사용될 수 있습니다).

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid,repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

여기서 `LibGit2.count`는 특정 `GitHash`와 함께 탐색하는 동안의 커밋 수를 찾습니다. `GitHash`는 커밋에 고유하므로, `cnt`는 `1`이 됩니다.
