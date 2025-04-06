```
cholesky!(A::AbstractMatrix, RowMaximum(); tol = 0.0, check = true) -> CholeskyPivoted
```

[`cholesky`](@ref)와 동일하지만, 복사본을 생성하는 대신 입력 `A`를 덮어써서 공간을 절약합니다. 인수 분해가 `A`의 요소 유형으로 표현할 수 없는 숫자를 생성하는 경우, 예를 들어 정수 유형의 경우 [`InexactError`](@ref) 예외가 발생합니다.
