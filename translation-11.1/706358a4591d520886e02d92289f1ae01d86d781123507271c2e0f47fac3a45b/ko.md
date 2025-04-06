```
sqrt(A::AbstractMatrix)
```

`A`에 음의 실 고유값이 없으면, `A`의 주 행렬 제곱근을 계산합니다. 즉, $X^2 = A$를 만족하고 고유값이 양의 실수 부분을 가지는 유일한 행렬 $X$입니다. 그렇지 않으면 비주 행렬 제곱근이 반환됩니다.

`A`가 실 대칭 행렬이거나 에르미트 행렬인 경우, 고유 분해([`eigen`](@ref))를 사용하여 제곱근을 계산합니다. 이러한 행렬의 경우, 반올림 오류로 인해 약간 음수로 나타나는 고유값 λ는 0으로 간주됩니다. 보다 정확하게, 모든 고유값이 `≥ -rtol*(max |λ|)`인 행렬은 반정의로 간주되어 (에르미트 제곱근을 생성함) 음의 고유값은 0으로 취급됩니다. `rtol`은 `sqrt`의 키워드 인수(에르미트/실 대칭 경우에만)로, 기본값은 `size(A,1)`에 의해 조정된 기계 정밀도입니다.

그렇지 않은 경우, 제곱근은 Björck-Hammarling 방법 [^BH83]에 의해 결정되며, 이는 복소수 슈르 형식([`schur`](@ref))을 계산한 다음 삼각 인자의 복소수 제곱근을 계산합니다. 실 제곱근이 존재하는 경우, 이 방법의 확장 [^H87]이 사용되어 실 슈르 형식을 계산한 다음 준삼각 인자의 실 제곱근을 계산합니다.

[^BH83]: Åke Björck and Sven Hammarling, "A Schur method for the square root of a matrix", Linear Algebra and its Applications, 52-53, 1983, 127-140. [doi:10.1016/0024-3795(83)80010-X](https://doi.org/10.1016/0024-3795(83)80010-X)

[^H87]: Nicholas J. Higham, "Computing real square roots of a real matrix", Linear Algebra and its Applications, 88-89, 1987, 405-430. [doi:10.1016/0024-3795(87)90118-2](https://doi.org/10.1016/0024-3795(87)90118-2)

# 예제

```jldoctest
julia> A = [4 0; 0 4]
2×2 Matrix{Int64}:
 4  0
 0  4

julia> sqrt(A)
2×2 Matrix{Float64}:
 2.0  0.0
 0.0  2.0
```
