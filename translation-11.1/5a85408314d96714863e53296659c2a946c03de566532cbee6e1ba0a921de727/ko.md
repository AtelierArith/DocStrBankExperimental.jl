```
lookup_branch(repo::GitRepo, branch_name::AbstractString, remote::Bool=false) -> Union{GitReference, Nothing}
```

지정된 `branch_name`에 해당하는 브랜치가 `repo` 리포지토리에 존재하는지 확인합니다. `remote`가 `true`인 경우, `repo`는 원격 git 리포지토리로 간주됩니다. 그렇지 않으면 로컬 파일 시스템의 일부입니다.

요청된 브랜치가 존재하는 경우 `GitReference`를 반환하고, 존재하지 않는 경우 [`nothing`](@ref)을 반환합니다.
