```
shuffle([rng=default_rng(),] v::AbstractArray)
```

返回 `v` 的一个随机排列副本。可选的 `rng` 参数指定一个随机数生成器（参见 [随机数](@ref)）。要就地排列 `v`，请参见 [`shuffle!`](@ref)。要获取随机排列的索引，请参见 [`randperm`](@ref)。

# 示例

```jldoctest
julia> shuffle(Xoshiro(123), Vector(1:10))
10-element Vector{Int64}:
  5
  4
  2
  3
  6
 10
  8
  1
  9
  7
```
