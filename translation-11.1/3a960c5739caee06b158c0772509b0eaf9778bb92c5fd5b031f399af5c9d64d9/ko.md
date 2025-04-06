```
UpperHessenberg(A::AbstractMatrix)
```

행렬 `A`의 `UpperHessenberg` 뷰를 생성합니다. 첫 번째 부대각선 아래의 `A`의 항목은 무시됩니다.

!!! compat "Julia 1.3"
    이 유형은 Julia 1.3에 추가되었습니다.


`H \ b`, `det(H)` 및 유사한 것들에 대해 효율적인 알고리즘이 구현되어 있습니다.

유사한 상부 헤센베르크 행렬로 모든 행렬을 인수분해하는 [`hessenberg`](@ref) 함수도 참조하십시오.

`F::Hessenberg`가 인수분해 객체인 경우, 유니타리 행렬은 `F.Q`로 접근할 수 있으며, 헤센베르크 행렬은 `F.H`로 접근할 수 있습니다. `Q`가 추출되면 결과 유형은 `HessenbergQ` 객체가 되며, [`convert(Array, _)`](@ref) (또는 짧게 `Array(_)`)를 사용하여 일반 행렬로 변환할 수 있습니다.

분해를 반복하면 인수 `F.Q`와 `F.H`가 생성됩니다.

# 예제

```jldoctest
julia> A = [1 2 3 4; 5 6 7 8; 9 10 11 12; 13 14 15 16]
4×4 Matrix{Int64}:
  1   2   3   4
  5   6   7   8
  9  10  11  12
 13  14  15  16

julia> UpperHessenberg(A)
4×4 UpperHessenberg{Int64, Matrix{Int64}}:
 1   2   3   4
 5   6   7   8
 ⋅  10  11  12
 ⋅   ⋅  15  16
```
