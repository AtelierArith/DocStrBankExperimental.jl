```
@sprintf("%Fmt", args...)
```

返回 [`@printf`](@ref) 格式化的输出作为字符串。

# 示例

```jldoctest
julia> @sprintf "this is a %s %15.1f" "test" 34.567
"this is a test            34.6"
```
