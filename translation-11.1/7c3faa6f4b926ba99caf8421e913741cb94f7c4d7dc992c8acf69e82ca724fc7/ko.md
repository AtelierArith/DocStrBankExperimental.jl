```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

현재 `GitConfig` `cfg`에 `path`에 위치한 기존 git 구성 파일을 추가합니다. 파일이 존재하지 않으면 생성됩니다.

  * `level`은 git 구성 우선 순위 수준을 설정하며, 이는

[`Consts.GIT_CONFIG`](@ref)에 의해 결정됩니다.

  * `repo`는 조건부 포함 구문 분석을 허용하는 선택적 저장소입니다.
  * `force`가 `false`이고 주어진 우선 순위 수준에 대한 구성이 이미 존재하는 경우,

`addfile`은 오류를 발생시킵니다. `force`가 `true`인 경우, 기존 구성은 `path`에 있는 파일의 구성으로 대체됩니다.
