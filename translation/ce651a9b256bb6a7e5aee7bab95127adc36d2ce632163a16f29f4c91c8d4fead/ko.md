```
ldlt!(F::CHOLMOD.Factor, A::SparseMatrixCSC; shift = 0.0, check = true) -> CHOLMOD.Factor
```

`A`의 $LDL'$ 분해를 계산하며, 기호 분해 `F`를 재사용합니다. `A`는 [`SparseMatrixCSC`](@ref) 또는 `SparseMatrixCSC`의 [`Symmetric`](@ref)/[`Hermitian`](@ref) 뷰여야 합니다. `A`가 타입 태그가 없더라도 여전히 대칭 또는 에르미트여야 합니다.

자세한 내용은 [`ldlt`](@ref)를 참조하세요.

!!! note
    이 메서드는 [SuiteSparse](https://github.com/DrTimothyAldenDavis/SuiteSparse)에서 제공하는 CHOLMOD 라이브러리를 사용하며, 이는 단일 또는 이중 정밀도의 실수 또는 복소수 타입만 지원합니다. 해당 요소 타입이 아닌 입력 행렬은 적절하게 이러한 타입으로 변환됩니다.

