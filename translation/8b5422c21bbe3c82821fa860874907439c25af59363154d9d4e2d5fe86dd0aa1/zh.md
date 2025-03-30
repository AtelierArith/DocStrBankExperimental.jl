```
coalesce(x...)
```

返回参数中第一个不等于 [`missing`](@ref) 的值（如果有的话）。否则返回 `missing`。

另请参见 [`skipmissing`](@ref), [`something`](@ref), [`@coalesce`](@ref)。

# 示例

```jldoctest
julia> coalesce(missing, 1)
1

julia> coalesce(1, missing)
1

julia> coalesce(nothing, 1)  # 返回 `nothing`

julia> coalesce(missing, missing)
missing
```
