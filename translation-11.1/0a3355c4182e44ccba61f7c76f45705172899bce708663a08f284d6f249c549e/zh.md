```
zip(iters...)
```

同时运行多个迭代器，直到其中任何一个耗尽。`zip` 迭代器的值类型是其子迭代器值的元组。

!!! note
    `zip` 以这样的方式对其子迭代器的调用进行排序，以便状态迭代器在当前迭代中另一个迭代器完成时不会前进。


!!! note
    `zip()` 没有参数时会产生一个无限的空元组迭代器。


另请参见: [`enumerate`](@ref), [`Base.splat`](@ref).

# 示例

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
