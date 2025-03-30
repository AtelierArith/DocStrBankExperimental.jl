```
get(val::ScopedValue{T})::Union{Nothing, Some{T}}
```

如果作用域值未设置且没有默认值，则返回 `nothing`。否则返回 `Some{T}`，其中包含当前值。

另请参见: [`ScopedValues.with`](@ref), [`ScopedValues.@with`](@ref), [`ScopedValues.ScopedValue`](@ref)。

# 示例

```jldoctest
julia> using Base.ScopedValues

julia> a = ScopedValue(42); b = ScopedValue{Int}();

julia> ScopedValues.get(a)
Some(42)

julia> isnothing(ScopedValues.get(b))
true
```
