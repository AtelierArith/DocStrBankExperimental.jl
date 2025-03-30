```
Symmetric(A::AbstractMatrix, uplo::Symbol=:U)
```

행렬 `A`의 상삼각형(만약 `uplo = :U`인 경우) 또는 하삼각형(만약 `uplo = :L`인 경우)의 `Symmetric` 뷰를 생성합니다.

`Symmetric` 뷰는 주로 실수 대칭 행렬에 유용하며, 이 행렬에 대해 특화된 알고리즘(예: 고유 문제 해결을 위한)이 `Symmetric` 타입에 대해 활성화됩니다. 더 일반적으로, 실수 행렬에 대해 `Symmetric`과 사실상 동등하지만 복소수 행렬에도 유용한 에르미트 행렬 `A == A'`에 대해서는 [`Hermitian(A)`](@ref)도 참조하십시오. (복소수 `Symmetric` 행렬은 지원되지만 특화된 알고리즘이 거의 없습니다.)

실수 행렬의 대칭 부분을 계산하거나, 더 일반적으로 실수 또는 복소수 행렬 `A`의 에르미트 부분 `(A + A') / 2`를 계산하려면 [`hermitianpart`](@ref)를 사용하십시오.

# 예제

```jldoctest
julia> A = [1 2 3; 4 5 6; 7 8 9]
3×3 Matrix{Int64}:
 1  2  3
 4  5  6
 7  8  9

julia> Supper = Symmetric(A)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  2  3
 2  5  6
 3  6  9

julia> Slower = Symmetric(A, :L)
3×3 Symmetric{Int64, Matrix{Int64}}:
 1  4  7
 4  5  8
 7  8  9

julia> hermitianpart(A)
3×3 Hermitian{Float64, Matrix{Float64}}:
 1.0  3.0  5.0
 3.0  5.0  7.0
 5.0  7.0  9.0
```

`Supper`는 `A`가 대칭 행렬(예: `A == transpose(A)`)이 아닌 한 `Slower`와 같지 않음을 유의하십시오.
