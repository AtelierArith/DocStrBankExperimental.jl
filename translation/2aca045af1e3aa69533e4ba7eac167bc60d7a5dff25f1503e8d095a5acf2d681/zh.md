```
middle(a::AbstractArray)
```

计算数组 `a` 的中间值，这包括找到其极值并计算它们的平均值。

```jldoctest
julia> using Statistics

julia> middle(1:10)
5.5

julia> a = [1,2,3.6,10.9]
4-element Vector{Float64}:
  1.0
  2.0
  3.6
 10.9

julia> middle(a)
5.95
```
