```
rand!([rng=default_rng()], A, [S=eltype(A)])
```

用随机值填充数组 `A`。如果指定了 `S`（`S` 可以是类型或集合，详见 [`rand`](@ref)），则值是从 `S` 中随机选择的。这相当于 `copyto!(A, rand(rng, S, size(A)))`，但不分配新的数组。

# 示例

```jldoctest
julia> rand!(Xoshiro(123), zeros(5))
5-element Vector{Float64}:
 0.521213795535383
 0.5868067574533484
 0.8908786980927811
 0.19090669902576285
 0.5256623915420473
```
