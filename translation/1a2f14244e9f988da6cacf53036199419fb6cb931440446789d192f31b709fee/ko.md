```
peel([T,] ref::GitReference)
```

`ref`를 재귀적으로 벗겨서 타입 `T`의 객체를 얻습니다. `T`가 제공되지 않으면, `ref`는 [`GitTag`](@ref)가 아닌 객체가 얻어질 때까지 벗겨집니다.

  * `GitTag`는 참조하는 객체로 벗겨집니다.
  * [`GitCommit`](@ref)는 [`GitTree`](@ref)로 벗겨집니다.

!!! note
    주석이 달린 태그만 `GitTag` 객체로 벗겨질 수 있습니다. 경량 태그(기본값)는 `refs/tags/` 아래의 참조로, 직접 `GitCommit` 객체를 가리킵니다.

