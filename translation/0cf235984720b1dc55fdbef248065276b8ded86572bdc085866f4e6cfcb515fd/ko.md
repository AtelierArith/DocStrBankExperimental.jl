```
ldlt(A::SparseMatrixCSC; shift = 0.0, check = true, perm=nothing) -> CHOLMOD.Factor
```

희소 행렬 `A`의 $LDL'$ 분해를 계산합니다. `A`는 [`SparseMatrixCSC`](@ref) 또는 `SparseMatrixCSC`의 [`Symmetric`](@ref)/[`Hermitian`](@ref) 뷰여야 합니다. `A`가 타입 태그가 없더라도 여전히 대칭 또는 에르미트여야 합니다. 채우기 감소 순열이 사용됩니다. `F = ldlt(A)`는 시스템의 방정식 `A*x = b`를 `F\b`로 해결하는 데 가장 자주 사용됩니다. 반환된 분해 객체 `F`는 또한 [`diag`](@ref), [`det`](@ref), [`logdet`](@ref), 및 [`inv`](@ref) 메서드를 지원합니다. `F`에서 개별 요소를 추출하려면 `F.L`을 사용하면 됩니다. 그러나 피벗이 기본적으로 활성화되어 있기 때문에, 분해는 내부적으로 `A == P'*L*D*L'*P`로 표현되며, 여기서 `P`는 순열 행렬입니다; `P`를 고려하지 않고 단순히 `L`을 사용하면 잘못된 결과가 나옵니다. 순열의 효과를 포함하려면, 일반적으로 `PtL = F.PtL` (즉, `P'*L`에 해당) 및 `LtP = F.UP` (즉, `L'*P`에 해당)와 같은 "결합된" 요소를 추출하는 것이 바람직합니다. 지원되는 요소의 전체 목록은 `:L, :PtL, :D, :UP, :U, :LD, :DU, :PtLD, :DUP`입니다.

`check = true`일 때, 분해가 실패하면 오류가 발생합니다. `check = false`일 때, 분해의 유효성을 확인하는 책임은 사용자에게 있습니다 (via [`issuccess`](@ref)).

선택적 `shift` 키워드 인수를 설정하면 `A` 대신 `A+shift*I`의 분해를 계산합니다. `perm` 인수가 제공되면, 이는 사용해야 할 순서를 제공하는 `1:size(A,1)`의 순열이어야 합니다 (CHOLMOD의 기본 AMD 순서 대신).

!!! note
    이 방법은 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse)에서 제공하는 CHOLMOD[^ACM887][^DavisHager2009] 라이브러리를 사용합니다. CHOLMOD는 단일 또는 이중 정밀도의 실수 또는 복소수 타입만 지원합니다. 해당 요소 타입이 아닌 입력 행렬은 적절하게 이러한 타입으로 변환됩니다.

    CHOLMOD의 많은 다른 함수가 래핑되었지만 `Base.SparseArrays.CHOLMOD` 모듈에서 내보내지지는 않았습니다.

