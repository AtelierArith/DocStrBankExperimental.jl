```
acos(A::AbstractMatrix)
```

정사각형 행렬 `A`의 역행렬 코사인을 계산합니다.

`A`가 대칭 또는 에르미트인 경우, 고유 분해([`eigen`](@ref))를 사용하여 역 코사인을 계산합니다. 그렇지 않은 경우, 역 코사인은 [`log`](@ref)와 [`sqrt`](@ref)를 사용하여 결정됩니다. 이 함수를 계산하는 데 사용되는 이론 및 로그 공식에 대한 내용은 [^AH16_1]을 참조하십시오.

[^AH16_1]: Mary Aprahamian과 Nicholas J. Higham, "Matrix Inverse Trigonometric and Inverse Hyperbolic Functions: Theory and Algorithms", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# 예제

```julia-repl
julia> acos(cos([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-8.32667e-17im  0.1+0.0im
 -0.2+2.63678e-16im  0.3-3.46945e-16im
```
