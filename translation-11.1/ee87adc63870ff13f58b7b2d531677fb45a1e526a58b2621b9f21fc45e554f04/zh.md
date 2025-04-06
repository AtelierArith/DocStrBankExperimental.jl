```
replace!(A, old_new::Pair...; [count::Integer])
```

对于每对 `old=>new` 在 `old_new` 中，将集合 `A` 中所有的 `old` 替换为 `new`。相等性使用 [`isequal`](@ref) 确定。如果指定了 `count`，则最多替换 `count` 次出现。另见 [`replace`](@ref replace(A, old_new::Pair...))。

# 示例

```jldoctest
julia> replace!([1, 2, 1, 3], 1=>0, 2=>4, count=2)
4-element Vector{Int64}:
 0
 4
 1
 3

julia> replace!(Set([1, 2, 3]), 1=>0)
Set{Int64} with 3 elements:
  0
  2
  3
```
