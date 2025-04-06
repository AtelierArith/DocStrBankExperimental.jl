```
LibGit2.count(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

[`GitRevWalker`](@ref) `walker`를 사용하여 저장소의 역사에서 모든 커밋을 "걷는" 동안, `f`가 적용될 때 `true`를 반환하는 커밋의 수를 찾습니다. 키워드 인자는 다음과 같습니다:     * `oid`: 걷기를 시작할 커밋의 [`GitHash`](@ref). 기본값은 [`push_head!`](@ref)를 사용하여 HEAD 커밋과 그 조상들을 사용하는 것입니다.     * `by`: 정렬 방법. 기본값은 정렬하지 않는 것입니다. 다른 옵션으로는 위상 정렬(`LibGit2.Consts.SORT_TOPOLOGICAL`), 시간 순으로 정렬(`LibGit2.Consts.SORT_TIME`, 가장 오래된 것 먼저) 또는 시간 역순으로 정렬(`LibGit2.Consts.SORT_REVERSE`, 가장 최근 것 먼저)이 있습니다.     * `rev`: 정렬된 순서를 뒤집을지 여부(예: 위상 정렬이 사용되는 경우).

# 예제

```julia
cnt = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.count((oid, repo)->(oid == commit_oid1), walker, oid=commit_oid1, by=LibGit2.Consts.SORT_TIME)
end
```

`LibGit2.count`는 특정 `GitHash` `commit_oid1`을 가진 커밋을 따라 걷는 동안의 커밋 수를 찾으며, 해당 커밋에서 시작하여 시간 순으로 앞으로 이동합니다. `GitHash`는 커밋에 고유하므로, `cnt`는 `1`이 됩니다.
