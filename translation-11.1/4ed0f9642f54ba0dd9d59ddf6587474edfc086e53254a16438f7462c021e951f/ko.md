```
LibGit2.workdir(repo::GitRepo)
```

`repo`의 작업 디렉토리 위치를 반환합니다. 이는 베어 리포지토리에서는 오류를 발생시킵니다.

!!! note
    일반적으로 이는 `gitdir(repo)`의 상위 디렉토리가 되지만, 경우에 따라 다를 수 있습니다: 예를 들어 `core.worktree` 구성 변수나 `GIT_WORK_TREE` 환경 변수가 설정된 경우입니다.


또한 [`gitdir`](@ref), [`path`](@ref)를 참조하세요.
