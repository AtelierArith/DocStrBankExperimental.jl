```
qr(A, pivot = NoPivot(); blocksize) -> F
```

행렬 `A`의 QR 분해를 계산합니다: 직교(또는 `A`가 복소수 값일 경우 유니타리) 행렬 `Q`와 상삼각 행렬 `R`이 있어 다음과 같은 관계를 만족합니다.

$$
A = Q R
$$

반환된 객체 `F`는 패킹된 형식으로 분해를 저장합니다:

  * `pivot == ColumnNorm()`인 경우 `F`는 [`QRPivoted`](@ref) 객체입니다.
  * 그렇지 않고 `A`의 요소 유형이 BLAS 유형([`Float32`](@ref), [`Float64`](@ref), `ComplexF32` 또는 `ComplexF64`)인 경우, `F`는 [`QRCompactWY`](@ref) 객체입니다.
  * 그렇지 않으면 `F`는 [`QR`](@ref) 객체입니다.

분해의 개별 구성 요소 `F`는 속성 접근자를 통해 검색할 수 있습니다:

  * `F.Q`: 직교/유니타리 행렬 `Q`
  * `F.R`: 상삼각 행렬 `R`
  * `F.p`: 피벗의 순열 벡터 ([`QRPivoted`](@ref) 전용)
  * `F.P`: 피벗의 순열 행렬 ([`QRPivoted`](@ref) 전용)

!!! note
    `F.R`를 통해 상삼각 요소에 대한 각 참조는 새로운 배열을 할당합니다. 따라서 `R = F.R`와 같이 해당 배열을 캐시하고 `R`로 계속 작업하는 것이 좋습니다.


분해를 반복하면 구성 요소 `Q`, `R`, 그리고 존재하는 경우 `p`를 생성합니다.

`QR` 객체에 대해 사용할 수 있는 함수는 다음과 같습니다: [`inv`](@ref), [`size`](@ref), 및 [`\`](@ref). `A`가 직사각형인 경우, `\`는 최소 제곱 해를 반환하며, 해가 유일하지 않은 경우 가장 작은 노름을 가진 해가 반환됩니다. `A`가 풀 랭크가 아닐 경우, 최소 노름 해를 얻기 위해 (열) 피벗을 사용한 분해가 필요합니다.

전체/정사각형 또는 비전체/비정사각형 `Q`에 대한 곱셈이 허용됩니다. 즉, `F.Q*F.R`와 `F.Q*A` 모두 지원됩니다. `Q` 행렬은 [`Matrix`](@ref)로 일반 행렬로 변환할 수 있습니다. 이 작업은 "얇은" Q 요소를 반환합니다. 즉, `A`가 `m`×`n`이고 `m>=n`인 경우, `Matrix(F.Q)`는 직교 정규 열을 가진 `m`×`n` 행렬을 생성합니다. "전체" Q 요소를 검색하려면 `F.Q*I` 또는 `collect(F.Q)`를 사용하십시오. `m<=n`인 경우, `Matrix(F.Q)`는 `m`×`m` 직교 행렬을 생성합니다.

QR 분해를 위한 블록 크기는 `pivot == NoPivot()`이고 `A isa StridedMatrix{<:BlasFloat}`일 때 키워드 인수 `blocksize :: Integer`로 지정할 수 있습니다. `blocksize > minimum(size(A))`인 경우 무시됩니다. [`QRCompactWY`](@ref)를 참조하십시오.

!!! compat "Julia 1.4"
    `blocksize` 키워드 인수는 Julia 1.4 이상이 필요합니다.


# 예제

```jldoctest
julia> A = [3.0 -6.0; 4.0 -8.0; 0.0 1.0]
3×2 Matrix{Float64}:
 3.0  -6.0
 4.0  -8.0
 0.0   1.0

julia> F = qr(A)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Q 요소: 3×3 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
R 요소:
2×2 Matrix{Float64}:
 -5.0  10.0
  0.0  -1.0

julia> F.Q * F.R == A
true
```

!!! note
    `qr`는 LAPACK가 Householder 기본 반사체의 곱의 메모리 저장 요구 사항을 최소화하는 여러 표현을 사용하기 때문에 여러 유형을 반환합니다. 따라서 `Q` 및 `R` 행렬을 두 개의 개별 밀집 행렬 대신 압축하여 저장할 수 있습니다.

