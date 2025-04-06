```
Base.depwarn(msg::String, funcsym::Symbol; force=false)
```

打印 `msg` 作为弃用警告。符号 `funcsym` 应该是调用函数的名称，用于确保弃用警告仅在每个调用位置第一次打印。设置 `force=true` 以强制始终显示警告，即使 Julia 是以 `--depwarn=no` 启动的（默认情况下）。

另见 [`@deprecate`](@ref)。

# 示例

```julia
function deprecated_func()
    Base.depwarn("Don't use `deprecated_func()`!", :deprecated_func)

    1 + 1
end
```
