```
ismutable(v) -> Bool
```

仅当值 `v` 是可变的时返回 `true`。有关不可变性的讨论，请参见 [Mutable Composite Types](@ref)。请注意，此函数作用于值，因此如果您给它一个 `DataType`，它会告诉您该类型的值是可变的。

!!! note
    出于技术原因，`ismutable` 对某些特殊类型的值（例如 `String` 和 `Symbol`）返回 `true`，尽管它们不能以允许的方式被修改。


另请参见 [`isbits`](@ref)，[`isstructtype`](@ref)。

# 示例

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! compat "Julia 1.5"
    此函数至少需要 Julia 1.5。

