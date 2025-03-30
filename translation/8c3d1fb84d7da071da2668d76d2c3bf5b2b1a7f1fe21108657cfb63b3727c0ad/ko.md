```
LibGit2.rebase!(repo::GitRepo, upstream::AbstractString="", newbase::AbstractString="")
```

현재 브랜치에서 자동 병합 리베이스를 시도합니다. 제공된 경우 `upstream`에서, 그렇지 않으면 업스트림 추적 브랜치에서 수행됩니다. `newbase`는 리베이스할 브랜치입니다. 기본적으로 이는 `upstream`입니다.

자동으로 해결할 수 없는 충돌이 발생하면 리베이스가 중단되며, 저장소와 작업 트리는 원래 상태로 남아 있고, 함수는 `GitError`를 발생시킵니다. 이는 대략 다음 명령어와 같습니다:

```
git rebase --merge [<upstream>]
if [ -d ".git/rebase-merge" ]; then
    git rebase --abort
fi
```
