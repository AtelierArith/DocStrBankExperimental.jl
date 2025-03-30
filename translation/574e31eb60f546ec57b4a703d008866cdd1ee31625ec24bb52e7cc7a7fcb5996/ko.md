```
cholesky(A::SparseMatrixCSC; shift = 0.0, check = true, perm = nothing) -> CHOLMOD.Factor
```

희소 양의 정부호 행렬 `A`의 Cholesky 분해를 계산합니다. `A`는 [`SparseMatrixCSC`](@ref) 또는 `SparseMatrixCSC`의 [`Symmetric`](@ref)/[`Hermitian`](@ref) 뷰여야 합니다. `A`가 타입 태그가 없더라도 여전히 대칭 또는 에르미트여야 합니다. `perm`이 주어지지 않으면, 채우기 감소 순열이 사용됩니다. `F = cholesky(A)`는 `F\b`로 방정식 시스템을 해결하는 데 가장 자주 사용되지만, [`diag`](@ref), [`det`](@ref), 및 [`logdet`](@ref)와 같은 메서드도 `F`에 대해 정의되어 있습니다. `F`에서 개별 요소를 추출할 수도 있으며, `F.L`을 사용할 수 있습니다. 그러나 피벗이 기본적으로 활성화되어 있기 때문에, 분해는 내부적으로 `A == P'*L*L'*P`로 표현되며, 여기서 `P`는 순열 행렬입니다. `P`를 고려하지 않고 단순히 `L`을 사용하면 잘못된 결과가 나옵니다. 순열의 효과를 포함하려면, 일반적으로 `PtL = F.PtL`(즉, `P'*L`) 및 `LtP = F.UP`(즉, `L'*P`)와 같은 "결합된" 요소를 추출하는 것이 바람직합니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다(즉, [`issuccess`](@ref) 사용).

선택적 `shift` 키워드 인수를 설정하면 `A` 대신 `A+shift*I`의 분해를 계산합니다. `perm` 인수가 제공되면, 이는 사용해야 할 순서를 제공하는 `1:size(A,1)`의 순열이어야 합니다(즉, CHOLMOD의 기본 AMD 순서 대신).

# 예제

다음 예제에서 사용된 채우기 감소 순열은 `[3, 2, 1]`입니다. `perm`이 `1:3`으로 설정되어 순열이 없도록 강제하면, 요소의 수는 6입니다.

```jldoctest
julia> A = [2 1 1; 1 2 0; 1 0 2]
3×3 Matrix{Int64}:
 2  1  1
 1  2  0
 1  0  2

julia> C = cholesky(sparse(A))
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  5
nnz:     5
success: true

julia> C.p
3-element Vector{Int64}:
 3
 2
 1

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421   0.0       0.0
 0.0       1.41421   0.0
 0.707107  0.707107  1.0

julia> L * L' ≈ A[C.p, C.p]
true

julia> P = sparse(1:3, C.p, ones(3))
3×3 SparseMatrixCSC{Float64, Int64} with 3 stored entries:
  ⋅    ⋅   1.0
  ⋅   1.0   ⋅
 1.0   ⋅    ⋅

julia> P' * L * L' * P ≈ A
true

julia> C = cholesky(sparse(A), perm=1:3)
SparseArrays.CHOLMOD.Factor{Float64, Int64}
type:    LLt
method:  simplicial
maxnnz:  6
nnz:     6
success: true

julia> L = sparse(C.L);

julia> Matrix(L)
3×3 Matrix{Float64}:
 1.41421    0.0       0.0
 0.707107   1.22474   0.0
 0.707107  -0.408248  1.1547

julia> L * L' ≈ A
true
```

!!! note
    이 방법은 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse)에서 CHOLMOD[^ACM887][^DavisHager2009] 라이브러리를 사용합니다. CHOLMOD는 단일 또는 이중 정밀도의 실수 또는 복소수 유형만 지원합니다. 이러한 요소 유형이 아닌 입력 행렬은 적절하게 이러한 유형으로 변환됩니다.

    CHOLMOD의 많은 다른 함수가 래핑되었지만 `Base.SparseArrays.CHOLMOD` 모듈에서 내보내지지는 않았습니다.


[^ACM887]: Chen, Y., Davis, T. A., Hager, W. W., & Rajamanickam, S. (2008). Algorithm 887: CHOLMOD, Supernodal Sparse Cholesky Factorization and Update/Downdate. ACM Trans. Math. Softw., 35(3). [doi:10.1145/1391989.1391995](https://doi.org/10.1145/1391989.1391995)

[^DavisHager2009]: Davis, Timothy A., & Hager, W. W. (2009). Dynamic Supernodes in Sparse Cholesky Update/Downdate and Triangular Solves. ACM Trans. Math. Softw., 35(4). [doi:10.1145/1462173.1462176](https://doi.org/10.1145/1462173.1462176)
