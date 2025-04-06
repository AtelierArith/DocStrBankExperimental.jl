```
branch!(repo::GitRepo, branch_name::AbstractString, commit::AbstractString=""; kwargs...)
```

`repo` 저장소에서 새로운 git 브랜치를 체크아웃합니다. `commit`은 새로운 브랜치의 시작점이 될 문자열 형태의 [`GitHash`](@ref)입니다. `commit`이 빈 문자열인 경우 현재 HEAD가 사용됩니다.

키워드 인자는 다음과 같습니다:

  * `track::AbstractString=""`: 이 새로운 브랜치가 추적해야 하는 원격 브랜치의 이름입니다. 비어 있으면(기본값) 원격 브랜치를 추적하지 않습니다.
  * `force::Bool=false`: `true`인 경우 브랜치 생성이 강제로 이루어집니다.
  * `set_head::Bool=true`: `true`인 경우 브랜치 생성이 완료된 후 브랜치 헤드가 `repo`의 HEAD로 설정됩니다.

`git checkout [-b|-B] <branch_name> [<commit>] [--track <track>]`와 동등합니다.

# 예제

```julia
repo = LibGit2.GitRepo(repo_path)
LibGit2.branch!(repo, "new_branch", set_head=false)
```
