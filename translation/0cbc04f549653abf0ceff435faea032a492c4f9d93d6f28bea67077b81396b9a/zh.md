```
filter(f, a)
```

返回集合 `a` 的副本，移除 `f` 为 `false` 的元素。函数 `f` 接受一个参数。

!!! compat "Julia 1.4"
    将 `a` 作为元组的支持至少需要 Julia 1.4。


另请参见: [`filter!`](@ref), [`Iterators.filter`](@ref).

# 示例

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
