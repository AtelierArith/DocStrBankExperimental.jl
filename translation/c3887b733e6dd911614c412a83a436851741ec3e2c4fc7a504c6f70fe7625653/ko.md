```
lu!(A, pivot = RowMaximum(); check = true, allowsingular = false) -> LU
```

`lu!`는 [`lu`](@ref)와 동일하지만 입력 `A`를 덮어써서 공간을 절약합니다. 인수 분해가 `A`의 요소 유형으로 표현할 수 없는 숫자를 생성하는 경우, 예를 들어 정수 유형의 경우, [`InexactError`](@ref) 예외가 발생합니다.

!!! compat "Julia 1.11"
    `allowsingular` 키워드 인자는 Julia 1.11에서 추가되었습니다.


# 예제

```jldoctest
julia> A = [4. 3.; 6. 3.]
2×2 Matrix{Float64}:
 4.0  3.0
 6.0  3.0

julia> F = lu!(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L 인자:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U 인자:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> iA = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> lu!(iA)
ERROR: InexactError: Int64(0.6666666666666666)
Stacktrace:
[...]
```
