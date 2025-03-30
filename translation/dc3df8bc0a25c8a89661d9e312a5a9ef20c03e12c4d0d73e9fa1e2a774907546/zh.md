```
tanh(x)
```

计算 `x` 的双曲正切。

另见 [`tan`](@ref), [`atanh`](@ref)。

# 示例

```jldoctest
julia> tanh.(-3:3f0)  # 这里 3f0 是 Float32
7-element Vector{Float32}:
 -0.9950548
 -0.9640276
 -0.7615942
  0.0
  0.7615942
  0.9640276
  0.9950548

julia> tan.(im .* (1:3))
3-element Vector{ComplexF64}:
 0.0 + 0.7615941559557649im
 0.0 + 0.9640275800758169im
 0.0 + 0.9950547536867306im
```
