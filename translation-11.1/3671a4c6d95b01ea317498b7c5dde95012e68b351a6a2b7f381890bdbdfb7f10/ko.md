```
lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC; check=true, reuse_symbolic=true, q=nothing) -> F::UmfpackLU
```

희소 행렬 `A`의 LU 분해를 계산하며, 이미 존재하는 LU 분해가 저장된 `F`의 기호 분해를 재사용합니다. `reuse_symbolic`이 false로 설정되지 않는 한, 희소 행렬 `A`는 LU 분해 `F`를 생성하는 데 사용된 행렬과 동일한 비영(非零) 패턴을 가져야 하며, 그렇지 않으면 오류가 발생합니다. `A`와 `F`의 크기가 다르면 모든 벡터가 그에 맞게 크기가 조정됩니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다 (via [`issuccess`](@ref)).

순열 `q`는 순열 벡터이거나 `nothing`일 수 있습니다. 순열 벡터가 제공되지 않거나 `q`가 `nothing`인 경우, UMFPACK의 기본값이 사용됩니다. 순열이 0 기반이 아닐 경우, 0 기반 복사가 이루어집니다.

자세한 내용은 [`lu`](@ref)를 참조하십시오.

!!! note
    `lu!(F::UmfpackLU, A::AbstractSparseMatrixCSC)`는 SuiteSparse의 일부인 UMFPACK 라이브러리를 사용합니다. 이 라이브러리는 [`Float64`](@ref) 또는 `ComplexF64` 요소를 가진 희소 행렬만 지원하므로, `lu!`는 LU 분해에 의해 설정된 유형이나 적절한 경우 `SparseMatrixCSC{ComplexF64}`로 자동 변환됩니다.


!!! compat "Julia 1.5"
    `UmfpackLU`에 대한 `lu!`는 최소한 Julia 1.5가 필요합니다.


# 예제

```jldoctest
julia> A = sparse(Float64[1.0 2.0; 0.0 3.0]);

julia> F = lu(A);

julia> B = sparse(Float64[1.0 1.0; 0.0 1.0]);

julia> lu!(F, B);

julia> F \ ones(2)
2-element Vector{Float64}:
 0.0
 1.0
```
