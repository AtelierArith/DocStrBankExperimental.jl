```
entrytype(te::GitTreeEntry)
```

`te`가 참조하는 객체의 유형을 반환합니다. 결과는 [`objtype`](@ref)가 반환하는 유형 중 하나가 될 것입니다. 예를 들어, `GitTree` 또는 `GitBlob`입니다.
