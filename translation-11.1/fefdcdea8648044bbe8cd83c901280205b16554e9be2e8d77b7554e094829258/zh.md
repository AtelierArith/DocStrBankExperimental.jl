```
Iterators.map(f, iterators...)
```

创建一个惰性映射。这是写成 `(f(args...) for args in zip(iterators...))` 的另一种语法。

!!! compat "Julia 1.6"
    此函数至少需要 Julia 1.6。


# 示例

```jldoctest
julia> collect(Iterators.map(x -> x^2, 1:3))
3-element Vector{Int64}:
 1
 4
 9
```
