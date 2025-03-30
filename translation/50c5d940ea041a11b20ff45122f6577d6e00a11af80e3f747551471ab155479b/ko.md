```
GitAnnotated(repo::GitRepo, commit_id::GitHash)
GitAnnotated(repo::GitRepo, ref::GitReference)
GitAnnotated(repo::GitRepo, fh::FetchHead)
GitAnnotated(repo::GitRepo, committish::AbstractString)
```

주석이 달린 git 커밋은 어떻게 조회되었는지와 그 이유에 대한 정보를 담고 있어, 리베이스나 병합 작업이 커밋의 맥락에 대한 더 많은 정보를 가질 수 있도록 합니다. 충돌 파일은 예를 들어 충돌하는 병합의 소스/대상 브랜치에 대한 정보를 포함합니다. 주석이 달린 커밋은 예를 들어 [`FetchHead`](@ref)가 전달될 때 원격 브랜치의 끝을 참조하거나 `GitReference`를 사용하여 설명된 브랜치 헤드를 참조할 수 있습니다.
