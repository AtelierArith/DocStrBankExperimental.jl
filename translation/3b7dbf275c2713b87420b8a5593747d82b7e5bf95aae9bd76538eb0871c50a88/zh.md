```
findmax(f, domain) -> (f(x), index)
```

返回一个值对，该值对包含在值域中的一个值（`f` 的输出）和在 `domain` 中对应值的索引或键（`f` 的输入），使得 `f(x)` 达到最大值。如果存在多个最大点，则返回第一个。

`domain` 必须是一个非空的可迭代对象，支持 [`keys`](@ref)。索引与 [`keys(domain)`](@ref) 返回的类型相同。

值的比较使用 `isless`。

!!! compat "Julia 1.7"
    此方法需要 Julia 1.7 或更高版本。


# 示例

```jldoctest
julia> findmax(identity, 5:9)
(9, 5)

julia> findmax(-, 1:10)
(-1, 1)

julia> findmax(first, [(1, :a), (3, :b), (3, :c)])
(3, 2)

julia> findmax(cos, 0:π/2:2π)
(1.0, 1)
```
