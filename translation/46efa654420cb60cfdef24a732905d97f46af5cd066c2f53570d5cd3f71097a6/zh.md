```
splat(f)
```

等价于

```julia
    my_splat(f) = args->f(args...)
```

即，给定一个函数，返回一个新的函数，该函数接受一个参数并将其展开到原始函数中。这在将多参数函数作为期望单个参数的上下文中的适配器时非常有用，但将元组作为该单个参数传递。

# 示例

```jldoctest
julia> map(splat(+), zip(1:3,4:6))
3-element Vector{Int64}:
 5
 7
 9

julia> my_add = splat(+)
splat(+)

julia> my_add((1,2,3))
6
```
