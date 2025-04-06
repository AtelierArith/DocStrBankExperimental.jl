```
Iterators.accumulate(f, itr; [init])
```

给定一个具有两个参数的函数 `f` 和一个迭代器 `itr`，返回一个新的迭代器，该迭代器依次将 `f` 应用到前一个值和 `itr` 的下一个元素。

这实际上是 [`Base.accumulate`](@ref) 的惰性版本。

!!! compat "Julia 1.5"
    关键字参数 `init` 在 Julia 1.5 中添加。


# 示例

```jldoctest
julia> a = Iterators.accumulate(+, [1,2,3,4]);

julia> foreach(println, a)
1
3
6
10

julia> b = Iterators.accumulate(/, (2, 5, 2, 5); init = 100);

julia> collect(b)
4-element Vector{Float64}:
 50.0
 10.0
  5.0
  1.0
```
