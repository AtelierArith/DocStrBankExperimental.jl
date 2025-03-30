```
cholesky!(A::AbstractMatrix, NoPivot(); check = true) -> Cholesky
```

[`cholesky`](@ref)와 동일하지만, 입력 `A`를 복사하는 대신 덮어써서 공간을 절약합니다. 인수 분해가 `A`의 요소 유형으로 표현할 수 없는 숫자를 생성하는 경우, 예를 들어 정수 유형의 경우, [`InexactError`](@ref) 예외가 발생합니다.

# 예제

```jldoctest
julia> A = [1 2; 2 50]
2×2 Matrix{Int64}:
 1   2
 2  50

julia> cholesky!(A)
ERROR: InexactError: Int64(6.782329983125268)
Stacktrace:
[...]
```
