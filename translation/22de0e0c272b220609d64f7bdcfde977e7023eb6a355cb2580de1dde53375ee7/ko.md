```
restore(s::State, repo::GitRepo)
```

저장소 `repo`를 이전 `State` `s`로 복원합니다. 예를 들어, 병합 시도 이전의 브랜치 HEAD로 복원할 수 있습니다. `s`는 [`snapshot`](@ref) 함수를 사용하여 생성할 수 있습니다.
