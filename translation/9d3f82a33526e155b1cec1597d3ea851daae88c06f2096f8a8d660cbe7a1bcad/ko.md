```
snapshot(repo::GitRepo) -> State
```

현재 저장소 `repo`의 상태를 스냅샷으로 저장하여 현재 HEAD, 인덱스 및 커밋되지 않은 작업을 저장합니다. 출력 `State`는 나중에 [`restore`](@ref) 호출 시 스냅샷된 상태로 저장소를 되돌리는 데 사용할 수 있습니다.
