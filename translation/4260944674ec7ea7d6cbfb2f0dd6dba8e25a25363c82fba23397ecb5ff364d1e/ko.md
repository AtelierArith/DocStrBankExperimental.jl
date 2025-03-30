```
merge_base(repo::GitRepo, one::AbstractString, two::AbstractString) -> GitHash
```

`one`과 `two` 커밋 간의 병합 기준(공통 조상)을 찾습니다. `one`과 `two`는 모두 문자열 형식일 수 있습니다. 병합 기준의 `GitHash`를 반환합니다.
