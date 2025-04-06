```
LibGit2.create_branch(repo::GitRepo, bname::AbstractString, commit_obj::GitCommit; force::Bool=false)
```

저장소 `repo`에 이름 `bname`을 가진 새 브랜치를 생성하고, 이는 커밋 `commit_obj`를 가리킵니다(이는 `repo`의 일부여야 합니다). `force`가 `true`인 경우, 이미 존재하는 `bname`이라는 이름의 브랜치를 덮어씁니다. `force`가 `false`이고 이미 `bname`이라는 이름의 브랜치가 존재하는 경우, 이 함수는 오류를 발생시킵니다.
