```
something(x...)
```

返回参数中第一个不等于 [`nothing`](@ref) 的值（如果有的话）。否则抛出错误。类型为 [`Some`](@ref) 的参数会被解包。

另请参见 [`coalesce`](@ref), [`skipmissing`](@ref), [`@something`](@ref)。

# 示例

```jldoctest
julia> something(nothing, 1)
1

julia> something(Some(1), nothing)
1

julia> something(Some(nothing), 2) === nothing
true

julia> something(missing, nothing)
missing

julia> something(nothing, nothing)
ERROR: ArgumentError: No value arguments present
```
