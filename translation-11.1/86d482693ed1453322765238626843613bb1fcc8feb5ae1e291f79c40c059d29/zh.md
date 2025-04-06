```
Hermitian(A::AbstractMatrix, uplo::Symbol=:U)
```

构造一个 `Hermitian` 视图，表示矩阵 `A` 的上三角（如果 `uplo = :U`）或下三角（如果 `uplo = :L`）。

要计算 `A` 的 Hermitian 部分，请使用 [`hermitianpart`](@ref)。

# 示例

```jldoctest
julia> A = [1 2+2im 3-3im; 4 5 6-6im; 7 8+8im 9]
3×3 Matrix{Complex{Int64}}:
 1+0im  2+2im  3-3im
 4+0im  5+0im  6-6im
 7+0im  8+8im  9+0im

julia> Hupper = Hermitian(A)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  2+2im  3-3im
 2-2im  5+0im  6-6im
 3+3im  6+6im  9+0im

julia> Hlower = Hermitian(A, :L)
3×3 Hermitian{Complex{Int64}, Matrix{Complex{Int64}}}:
 1+0im  4+0im  7+0im
 4+0im  5+0im  8-8im
 7+0im  8+8im  9+0im

julia> hermitianpart(A)
3×3 Hermitian{ComplexF64, Matrix{ComplexF64}}:
 1.0+0.0im  3.0+1.0im  5.0-1.5im
 3.0-1.0im  5.0+0.0im  7.0-7.0im
 5.0+1.5im  7.0+7.0im  9.0+0.0im
```

请注意，除非 `A` 本身是 Hermitian（例如，如果 `A == adjoint(A)`），否则 `Hupper` 将不等于 `Hlower`。

对角线的所有非实部将被忽略。

```julia
Hermitian(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
