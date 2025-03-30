```
shuffle!([rng=default_rng(),] v::AbstractArray)
```

[`shuffle`](@ref) 的就地版本：随机地就地排列 `v`，可选地提供随机数生成器 `rng`。

# 示例

```jldoctest
julia> shuffle!(Xoshiro(123), Vector(1:10))
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
