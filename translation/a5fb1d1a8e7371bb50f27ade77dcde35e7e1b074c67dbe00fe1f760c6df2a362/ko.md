```
clone(repo_url::AbstractString, repo_path::AbstractString; kwargs...)
```

원격 저장소 `repo_url`를 로컬 파일 시스템 위치 `repo_path`로 복제합니다.

키워드 인자는 다음과 같습니다:

  * `branch::AbstractString=""`: 기본 저장소 브랜치(보통 `master`)가 아닌 경우 복제할 원격 브랜치입니다.
  * `isbare::Bool=false`: `true`인 경우, 원격을 베어 저장소로 복제하며, 이 경우 `repo_path` 자체가 git 디렉토리가 되고 `repo_path/.git`가 아닙니다. 이는 작업 트리를 체크아웃할 수 없음을 의미합니다. git CLI 인수 `--bare`의 역할을 합니다.
  * `remote_cb::Ptr{Cvoid}=C_NULL`: 복제하기 전에 원격을 생성하는 데 사용될 콜백입니다. `C_NULL`(기본값)인 경우, 원격을 생성하려고 시도하지 않으며, 이미 존재하는 것으로 간주됩니다.
  * `credentials::Creds=nothing`: 개인 저장소에 대한 인증 시 자격 증명 및/또는 설정을 제공합니다.
  * `callbacks::Callbacks=Callbacks()`: 사용자가 제공한 콜백 및 페이로드입니다.

`git clone [-b <branch>] [--bare] <repo_url> <repo_path>`와 동등합니다.

# 예제

```julia
repo_url = "https://github.com/JuliaLang/Example.jl"
repo1 = LibGit2.clone(repo_url, "test_path")
repo2 = LibGit2.clone(repo_url, "test_path", isbare=true)
julia_url = "https://github.com/JuliaLang/julia"
julia_repo = LibGit2.clone(julia_url, "julia_path", branch="release-0.6")
```
