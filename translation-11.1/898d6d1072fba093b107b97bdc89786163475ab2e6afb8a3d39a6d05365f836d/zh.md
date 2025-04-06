```
repeated(x[, n::Int])
```

一个生成值 `x` 的迭代器，永远生成。如果指定了 `n`，则生成 `x` 这么多次（等价于 `take(repeated(x), n)`）。

另请参见 [`fill`](@ref Base.fill)，并比较 [`Iterators.cycle`](@ref)。

# 示例

```jldoctest
julia> a = Iterators.repeated([1 2], 4);

julia> collect(a)
4-element Vector{Matrix{Int64}}:
 [1 2]
 [1 2]
 [1 2]
 [1 2]

julia> ans == fill([1 2], 4)
true

julia> Iterators.cycle([1 2], 4) |> collect |> println
[1, 2, 1, 2, 1, 2, 1, 2]
```
