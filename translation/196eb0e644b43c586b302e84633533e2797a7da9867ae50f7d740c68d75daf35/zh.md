```
isbitstype(T)
```

如果类型 `T` 是一种“简单数据”类型，则返回 `true`，这意味着它是不可变的，并且不包含对其他值的引用，仅包含 `primitive` 类型和其他 `isbitstype` 类型。典型示例包括数字类型，如 [`UInt8`](@ref)、[`Float64`](@ref) 和 [`Complex{Float64}`](@ref)。这一类类型是重要的，因为它们可以作为类型参数，可能不跟踪 [`isdefined`](@ref) / [`isassigned`](@ref) 状态，并且具有与 C 兼容的定义布局。如果 `T` 不是类型，则返回 `false`。

另请参见 [`isbits`](@ref)、[`isprimitivetype`](@ref)、[`ismutable`](@ref)。

# 示例

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
