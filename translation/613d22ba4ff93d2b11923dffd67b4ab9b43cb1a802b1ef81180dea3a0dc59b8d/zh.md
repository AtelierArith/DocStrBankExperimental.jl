```
GitConfig(path::AbstractString, level::Consts.GIT_CONFIG=Consts.CONFIG_LEVEL_APP, force::Bool=false)
```

通过从`path`处的文件加载配置信息来创建一个新的`GitConfig`。有关`level`、`repo`和`force`选项的更多信息，请参见[`addfile`](@ref)。
