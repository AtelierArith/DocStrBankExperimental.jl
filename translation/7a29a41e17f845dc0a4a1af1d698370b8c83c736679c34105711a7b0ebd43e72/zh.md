```
mean(f, itr)
```

将函数 `f` 应用到集合 `itr` 的每个元素，并计算平均值。

```jldoctest
julia> using Statistics

julia> mean(√, [1, 2, 3])
1.3820881233139908

julia> mean([√1, √2, √3])
1.3820881233139908
```
