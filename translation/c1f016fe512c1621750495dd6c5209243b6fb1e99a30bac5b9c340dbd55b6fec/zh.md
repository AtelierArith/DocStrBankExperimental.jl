```
union!(s::Union{AbstractSet,AbstractVector}, itrs...)
```

构造传入集合的 [`union`](@ref) 并用结果覆盖 `s`。对于数组保持顺序。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> a = Set([3, 4, 5]);

julia> union!(a, 1:2:7);

julia> a
Set{Int64} with 5 elements:
  5
  4
  7
  3
  1
```
