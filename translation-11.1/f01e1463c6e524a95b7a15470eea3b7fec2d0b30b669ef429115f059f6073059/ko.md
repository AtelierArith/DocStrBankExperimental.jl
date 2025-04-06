```
LibGit2.status(repo::GitRepo, path::String) -> Union{Cuint, Cvoid}
```

`repo`에 있는 `path`의 파일 상태를 조회합니다. 예를 들어, 이 기능은 `path`의 파일이 수정되었는지 확인하고 스테이징 및 커밋이 필요한지 확인하는 데 사용할 수 있습니다.
