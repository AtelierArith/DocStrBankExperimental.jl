```
Bidiagonal(A, uplo::Symbol)
```

从 `A` 的主对角线及其第一个超对角线（如果 `uplo=:U`）或下对角线（如果 `uplo=:L`）构造一个 `Bidiagonal` 矩阵。

# 示例

```jldoctest
julia> A = [1 1 1 1; 2 2 2 2; 3 3 3 3; 4 4 4 4]
4×4 Matrix{Int64}:
 1  1  1  1
 2  2  2  2
 3  3  3  3
 4  4  4  4

julia> Bidiagonal(A, :U) # 包含 A 的主对角线和第一个超对角线
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  1  ⋅  ⋅
 ⋅  2  2  ⋅
 ⋅  ⋅  3  3
 ⋅  ⋅  ⋅  4

julia> Bidiagonal(A, :L) # 包含 A 的主对角线和第一个下对角线
4×4 Bidiagonal{Int64, Vector{Int64}}:
 1  ⋅  ⋅  ⋅
 2  2  ⋅  ⋅
 ⋅  3  3  ⋅
 ⋅  ⋅  4  4
```
