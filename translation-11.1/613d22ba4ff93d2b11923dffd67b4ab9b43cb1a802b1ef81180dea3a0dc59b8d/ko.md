```
GitConfig(path::AbstractString, level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP, force::Bool=false)
```

`path`에 있는 파일에서 구성 정보를 로드하여 새로운 `GitConfig`를 생성합니다. `level`, `repo` 및 `force` 옵션에 대한 자세한 내용은 [`addfile`](@ref)를 참조하십시오.
