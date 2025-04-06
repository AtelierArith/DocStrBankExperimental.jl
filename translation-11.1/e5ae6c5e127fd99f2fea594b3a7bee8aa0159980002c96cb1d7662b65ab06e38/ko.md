```
LibGit2.init(path::AbstractString, bare::Bool=false) -> GitRepo
```

`path`에 새 git 저장소를 엽니다. `bare`가 `false`인 경우 작업 트리가 `path/.git`에 생성됩니다. `bare`가 `true`인 경우 작업 디렉토리가 생성되지 않습니다.
