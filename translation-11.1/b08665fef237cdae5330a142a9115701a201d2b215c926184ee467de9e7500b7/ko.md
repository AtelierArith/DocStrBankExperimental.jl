```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!`는 `A`가 [`AbstractMatrix`](@ref)의 하위 유형일 때 [`qr`](@ref)와 동일하지만, 입력 `A`를 덮어써서 공간을 절약합니다. 인수 분해가 `A`의 요소 유형으로 표현할 수 없는 숫자를 생성하는 경우, 예를 들어 정수 유형의 경우, [`InexactError`](@ref) 예외가 발생합니다.

!!! compat "Julia 1.4"
    `blocksize` 키워드 인수는 Julia 1.4 이상이 필요합니다.


# 예제

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q 인자: 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R 인자:
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
ERROR: InexactError: Int64(3.1622776601683795)
Stacktrace:
[...]
```
