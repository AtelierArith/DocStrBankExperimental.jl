```
setdiff!(s, itrs...)
```

从集合 `s` 中（就地）移除每个可迭代对象 `itrs` 中的每个元素。使用数组时保持顺序。

!!! warning
    当任何被修改的参数与其他参数共享内存时，行为可能会出乎意料。


# 示例

```jldoctest
julia> a = Set([1, 3, 4, 5]);

julia> setdiff!(a, 1:2:6);

julia> a
Set{Int64} with 1 element:
  4
```
