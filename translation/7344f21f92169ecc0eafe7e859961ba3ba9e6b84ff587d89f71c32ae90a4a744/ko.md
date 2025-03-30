```
LibGit2.gitdir(repo::GitRepo)
```

`repo`의 "git" 파일의 위치를 반환합니다:

  * 일반 저장소의 경우, 이는 `.git` 폴더의 위치입니다.
  * 베어 저장소의 경우, 이는 저장소 자체의 위치입니다.

또한 [`workdir`](@ref), [`path`](@ref)를 참조하세요.
