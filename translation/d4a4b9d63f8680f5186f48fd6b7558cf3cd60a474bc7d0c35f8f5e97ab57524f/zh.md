```
@v_str
```

字符串宏用于将字符串解析为 [`VersionNumber`](@ref)。

# 示例

```jldoctest
julia> v"1.2.3"
v"1.2.3"

julia> v"2.0.1-rc1"
v"2.0.1-rc1"
```
