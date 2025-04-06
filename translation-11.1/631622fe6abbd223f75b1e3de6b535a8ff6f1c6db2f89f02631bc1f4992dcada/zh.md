```
replace(new::Union{Function, Type}, A; [count::Integer])
```

返回 `A` 的副本，其中 `A` 中的每个值 `x` 都被 `new(x)` 替换。如果指定了 `count`，则最多替换 `count` 个值（替换被定义为 `new(x) !== x`）。

!!! compat "Julia 1.7"
    需要版本 1.7 才能替换 `Tuple` 的元素。


# 示例

```jldoctest
julia> replace(x -> isodd(x) ? 2x : x, [1, 2, 3, 4])
4-element Vector{Int64}:
 2
 2
 6
 4

julia> replace(Dict(1=>2, 3=>4)) do kv
           first(kv) < 3 ? first(kv)=>3 : kv
       end
Dict{Int64, Int64} with 2 entries:
  3 => 4
  1 => 3
```
