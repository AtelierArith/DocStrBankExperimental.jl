```
Bidiagonal(dv::V, ev::V, uplo::Symbol) where V <: AbstractVector
```

使用给定的对角线 (`dv`) 和副对角线 (`ev`) 向量构造一个上三角 (`uplo=:U`) 或下三角 (`uplo=:L`) 的双对角矩阵。结果是 `Bidiagonal` 类型，并提供高效的专用线性求解器，但可以通过 [`convert(Array, _)`](@ref)（或简写为 `Array(_)`）转换为常规矩阵。`ev` 的长度必须比 `dv` 的长度少一个。

# 示例

```jldoctest
julia> dv = [1, 2, 3, 4]
4-element Vector{Int64}:
 1
 2
 3
 4

julia> ev = [7, 8, 9]
3-element Vector{Int64}:
 7
 8
 9

julia> Bu = Bidiagonal(dv, ev, :U) # ev 在第一个超对角线上
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  7  ⋅  ⋅
 ⋅  2  8  ⋅
 ⋅  ⋅  3  9
 ⋅  ⋅  ⋅  4

julia> Bl = Bidiagonal(dv, ev, :L) # ev 在第一个下对角线上
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 7  2  ⋅  ⋅
 ⋅  8  3  ⋅
 ⋅  ⋅  9  4
```
