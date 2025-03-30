```
findmin(f, domain) -> (f(x), index)
```

返回一个值对，该值对包含在值域中的一个值（`f` 的输出）和在 `domain` 中对应值的索引或键（`f` 的输入），使得 `f(x)` 被最小化。如果存在多个最小点，则返回第一个。

`domain` 必须是一个非空的可迭代对象。

索引与 [`keys(domain)`](@ref) 和 [`pairs(domain)`](@ref) 返回的类型相同。

`NaN` 被视为小于所有其他值，除了 `missing`。

!!! compat "Julia 1.7"
    此方法需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> findmin(identity, 5:9)
(5, 1)

julia> findmin(-, 1:10)
(-10, 10)

julia> findmin(first, [(2, :a), (2, :b), (3, :c)])
(2, 1)

julia> findmin(cos, 0:π/2:2π)
(-1.0, 3)
```
