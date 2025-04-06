```
typeassert(x, type)
```

除非 `x isa type`，否则抛出一个 [`TypeError`](@ref)。语法 `x::type` 调用此函数。

# 示例

```jldoctest
julia> typeassert(2.5, Int)
ERROR: TypeError: in typeassert, expected Int64, got a value of type Float64
Stacktrace:
[...]
```
