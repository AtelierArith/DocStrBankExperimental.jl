```
LibGit2.map(f::Function, walker::GitRevWalker; oid::GitHash=GitHash(), range::AbstractString="", by::Cint=Consts.SORT_NONE, rev::Bool=false)
```

[`GitRevWalker`](@ref) `walker`를 사용하여 저장소의 역사에서 모든 커밋을 "걷는" 동안, 각 커밋에 대해 `f`를 적용합니다. 키워드 인자는 다음과 같습니다:     * `oid`: 걷기를 시작할 커밋의 [`GitHash`](@ref). 기본값은 [`push_head!`](@ref)를 사용하여 HEAD 커밋과 그 조상들을 사용하는 것입니다.     * `range`: `oid1..oid2` 형식의 `GitHash` 범위. `f`는 두 커밋 사이의 모든 커밋에 적용됩니다.     * `by`: 정렬 방법. 기본값은 정렬하지 않는 것입니다. 다른 옵션으로는 위상 정렬(`LibGit2.Consts.SORT_TOPOLOGICAL`), 시간 순으로 정렬(`LibGit2.Consts.SORT_TIME`, 가장 오래된 것 먼저) 또는 시간 역순으로 정렬(`LibGit2.Consts.SORT_REVERSE`, 가장 최근 것 먼저)이 있습니다.     * `rev`: 정렬된 순서를 뒤집을지 여부(예: 위상 정렬이 사용되는 경우).

# 예제

```julia
oids = LibGit2.with(LibGit2.GitRevWalker(repo)) do walker
    LibGit2.map((oid, repo)->string(oid), walker, by=LibGit2.Consts.SORT_TIME)
end
```

여기서 `LibGit2.map`은 `GitRevWalker`를 사용하여 각 커밋을 방문하고 해당 `GitHash`를 찾습니다.
