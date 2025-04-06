```
asin(A::AbstractMatrix)
```

정사각형 행렬 `A`의 역행렬 사인 값을 계산합니다.

`A`가 대칭 또는 에르미트인 경우, 고유 분해([`eigen`](@ref))를 사용하여 역 사인을 계산합니다. 그렇지 않으면, 역 사인은 [`log`](@ref)와 [`sqrt`](@ref)를 사용하여 결정됩니다. 이 함수의 계산에 사용되는 이론과 로그 공식에 대한 내용은 [^AH16_2]를 참조하십시오.

[^AH16_2]: Mary Aprahamian과 Nicholas J. Higham, "행렬 역 삼각 함수 및 역 쌍곡선 함수: 이론 및 알고리즘", MIMS EPrint: 2016.4. [https://doi.org/10.1137/16M1057577](https://doi.org/10.1137/16M1057577)

# 예제

```julia-repl
julia> asin(sin([0.5 0.1; -0.2 0.3]))
2×2 Matrix{ComplexF64}:
  0.5-4.16334e-17im  0.1-5.55112e-17im
 -0.2+9.71445e-17im  0.3-1.249e-16im
```
