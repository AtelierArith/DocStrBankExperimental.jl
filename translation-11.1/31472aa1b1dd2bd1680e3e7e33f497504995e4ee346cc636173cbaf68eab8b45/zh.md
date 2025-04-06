```
x || y
```

短路布尔或。

另见：[`|`](@ref), [`xor`](@ref), [`&&`](@ref)。

# 示例

```jldoctest
julia> pi < 3 || ℯ < 3
true

julia> false || true || println("neither is true!")
true
```
