```
log(A::AbstractMatrix)
```

`A`에 음의 실 고유값이 없으면, `A`의 주 행렬 로그를 계산합니다. 즉, $e^X = A$이고 모든 고유값 $\lambda$에 대해 $-\pi < Im(\lambda) < \pi$인 유일한 행렬 $X$를 계산합니다. `A`에 비양수 고유값이 있는 경우, 가능한 경우 비주 행렬 함수가 반환됩니다.

`A`가 대칭 또는 에르미트인 경우, 그 고유 분해([`eigen`](@ref))가 사용되며, `A`가 삼각형인 경우에는 개선된 역 스케일링 및 제곱 방법이 사용됩니다(자세한 내용은 [^AH12] 및 [^AHR13] 참조). `A`가 음의 고유값이 없는 실수인 경우, 실 슈르 형식이 계산됩니다. 그렇지 않으면 복소 슈르 형식이 계산됩니다. 그런 다음 [^AHR13]의 상부 (준)삼각형 알고리즘이 상부 (준)삼각형 요소에 사용됩니다.

[^AH12]: Awad H. Al-Mohy와 Nicholas J. Higham, "Improved inverse scaling and squaring algorithms for the matrix logarithm", SIAM Journal on Scientific Computing, 34(4), 2012, C153-C169. [doi:10.1137/110852553](https://doi.org/10.1137/110852553)

[^AHR13]: Awad H. Al-Mohy, Nicholas J. Higham 및 Samuel D. Relton, "Computing the Fréchet derivative of the matrix logarithm and estimating the condition number", SIAM Journal on Scientific Computing, 35(4), 2013, C394-C410. [doi:10.1137/120885991](https://doi.org/10.1137/120885991)

# 예제

```jldoctest
julia> A = Matrix(2.7182818*I, 2, 2)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828

julia> log(A)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0
```
