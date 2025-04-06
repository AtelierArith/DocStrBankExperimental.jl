```
Array{T}(undef, dims)
Array{T,N}(undef, dims)
```

构造一个未初始化的 `N` 维 [`Array`](@ref)，其元素类型为 `T`。`N` 可以显式提供，如 `Array{T,N}(undef, dims)`，或者通过 `dims` 的长度或数量来确定。`dims` 可以是一个元组或一系列整数参数，对应于每个维度的长度。如果显式提供了秩 `N`，则它必须与 `dims` 的长度或数量匹配。这里 [`undef`](@ref) 是 [`UndefInitializer`](@ref)。

# 示例

```julia-repl
julia> A = Array{Float64, 2}(undef, 2, 3) # N 显式给出
2×3 Matrix{Float64}:
 6.90198e-310  6.90198e-310  6.90198e-310
 6.90198e-310  6.90198e-310  0.0

julia> B = Array{Float64}(undef, 4) # N 由输入确定
4-element Vector{Float64}:
   2.360075077e-314
 NaN
   2.2671131793e-314
   2.299821756e-314

julia> similar(B, 2, 4, 1) # 使用 typeof(B)，以及给定的大小
2×4×1 Array{Float64, 3}:
[:, :, 1] =
 2.26703e-314  2.26708e-314  0.0           2.80997e-314
 0.0           2.26703e-314  2.26708e-314  0.0
```
