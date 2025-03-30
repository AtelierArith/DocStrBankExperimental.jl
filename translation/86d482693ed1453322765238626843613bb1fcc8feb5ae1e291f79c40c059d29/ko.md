```
Hermitian(A::AbstractMatrix, uplo::Symbol=:U)
```

행렬 `A`의 상삼각형(만약 `uplo = :U`인 경우) 또는 하삼각형(만약 `uplo = :L`인 경우)의 `Hermitian` 뷰를 생성합니다.

`A`의 Hermitian 부분을 계산하려면 [`hermitianpart`](@ref)를 사용하세요.

# 예제

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

`Hupper`는 `A`가 자체적으로 Hermitian이 아닌 한 `Hlower`와 같지 않습니다(예: `A == adjoint(A)`인 경우).

대각선의 모든 비실수 부분은 무시됩니다.

```julia
Hermitian(fill(complex(1,1), 1, 1)) == fill(1, 1, 1)
```
