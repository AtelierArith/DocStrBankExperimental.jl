```
exp(A::AbstractMatrix)
```

행렬 `A`의 지수 행렬을 계산합니다. 이는 다음과 같이 정의됩니다.

$$
e^A = \sum_{n=0}^{\infty} \frac{A^n}{n!}.
$$

대칭 또는 에르미트 행렬 `A`의 경우 고유 분해([`eigen`](@ref))가 사용되며, 그렇지 않은 경우 스케일링 및 제곱 알고리즘이 선택됩니다(자세한 내용은 [^H05] 참조).

[^H05]: Nicholas J. Higham, "The squaring and scaling method for the matrix exponential revisited", SIAM Journal on Matrix Analysis and Applications, 26(4), 2005, 1179-1193. [doi:10.1137/090768539](https://doi.org/10.1137/090768539)

# 예제

```jldoctest
julia> A = Matrix(1.0I, 2, 2)
2×2 Matrix{Float64}:
 1.0  0.0
 0.0  1.0

julia> exp(A)
2×2 Matrix{Float64}:
 2.71828  0.0
 0.0      2.71828
```
