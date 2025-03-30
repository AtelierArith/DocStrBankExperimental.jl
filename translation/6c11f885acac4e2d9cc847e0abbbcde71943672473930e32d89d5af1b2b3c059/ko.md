```
upstream(ref::GitReference) -> Union{GitReference, Nothing}
```

`ref`를 포함하는 브랜치에 지정된 업스트림 브랜치가 있는지 확인합니다.

업스트림 브랜치가 존재하면 `GitReference`를 반환하고, 요청한 브랜치에 업스트림 대응 브랜치가 없으면 [`nothing`](@ref)을 반환합니다.
