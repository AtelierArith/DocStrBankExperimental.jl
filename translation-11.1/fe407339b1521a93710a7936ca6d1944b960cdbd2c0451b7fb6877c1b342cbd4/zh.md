```
isdir(path) -> Bool
```

如果 `path` 是一个目录，则返回 `true`，否则返回 `false`。

# 示例

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

另见 [`isfile`](@ref) 和 [`ispath`](@ref)。
