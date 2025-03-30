```
addfile(cfg::GitConfig, path::AbstractString,
        level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP,
        repo::Union{GitRepo, Nothing} = nothing,
        force::Bool=false)
```

将位于 `path` 的现有 git 配置文件添加到当前的 `GitConfig` `cfg`。如果文件不存在，将会创建它。

  * `level` 设置 git 配置的优先级，并由

[`Consts.GIT_CONFIG`](@ref) 决定。

  * `repo` 是一个可选的仓库，用于允许解析条件包含。
  * 如果 `force` 为 `false` 且给定优先级的配置已存在，

`addfile` 将会报错。如果 `force` 为 `true`，则现有配置将被 `path` 中的文件替换。
