```
supertypes(T::Type)
```

返回一个元组 `(T, ..., Any)`，其中包含 `T` 及其所有超类型，这些超类型通过对 [`supertype`](@ref) 函数的连续调用确定，按 `<:` 的顺序列出，并以 `Any` 结束。

另请参见 [`subtypes`](@ref)。

# 示例

```jldoctest
julia> supertypes(Int)
(Int64, Signed, Integer, Real, Number, Any)
```
