```
diagm(kv::Pair{<:Integer,<:AbstractVector}...)
diagm(m::Integer, n::Integer, kv::Pair{<:Integer,<:AbstractVector}...)
```

从对角线和向量的 `Pair` 构造一个矩阵。向量 `kv.second` 将被放置在 `kv.first` 对角线上。默认情况下，矩阵是方形的，其大小由 `kv` 推断，但可以通过将 `m,n` 作为第一个参数传递来指定非方形大小 `m`×`n`（根据需要用零填充）。对于重复的对角线索引 `kv.first`，对应向量 `kv.second` 中的值将被相加。

`diagm` 构造一个完整的矩阵；如果您想要存储效率高且运算快速的版本，请参见 [`Diagonal`](@ref)、[`Bidiagonal`](@ref) [`Tridiagonal`](@ref) 和 [`SymTridiagonal`](@ref)。

# 示例

```jldoctest
julia> diagm(1 => [1,2,3])
4×4 Matrix{Int64}:
 0  1  0  0
 0  0  2  0
 0  0  0  3
 0  0  0  0

julia> diagm(1 => [1,2,3], -1 => [4,5])
4×4 Matrix{Int64}:
 0  1  0  0
 4  0  2  0
 0  5  0  3
 0  0  0  0

julia> diagm(1 => [1,2,3], 1 => [1,2,3])
4×4 Matrix{Int64}:
 0  2  0  0
 0  0  4  0
 0  0  0  6
 0  0  0  0
```
