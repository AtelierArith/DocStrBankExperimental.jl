```
cycle(iter[, n::Int])
```

一个无限循环遍历 `iter` 的迭代器。如果指定了 `n`，则循环遍历 `iter` 该次数。当 `iter` 为空时，`cycle(iter)` 和 `cycle(iter, n)` 也为空。

`Iterators.cycle(iter, n)` 是 [`Base.repeat`](@ref)`(vector, n)` 的惰性等价，而 [`Iterators.repeated`](@ref)`(iter, n)` 是惰性 [`Base.fill`](@ref)`(item, n)`。

!!! compat "Julia 1.11"
    方法 `cycle(iter, n)` 在 Julia 1.11 中添加。


# 示例

```jldoctest
julia> for (i, v) in enumerate(Iterators.cycle("hello"))
           print(v)
           i > 10 && break
       end
hellohelloh

julia> foreach(print, Iterators.cycle(['j', 'u', 'l', 'i', 'a'], 3))
juliajuliajulia

julia> repeat([1,2,3], 4) == collect(Iterators.cycle([1,2,3], 4))
true

julia> fill([1,2,3], 4) == collect(Iterators.repeated([1,2,3], 4))
true
```
