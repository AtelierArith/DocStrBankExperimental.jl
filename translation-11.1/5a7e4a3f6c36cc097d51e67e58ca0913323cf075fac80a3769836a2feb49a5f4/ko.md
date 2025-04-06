```
cbrt(A::AbstractMatrix{<:Real})
```

실수 행렬 `A`의 실수 값 세제곱근을 계산합니다. `T = cbrt(A)`인 경우, `T*T*T ≈ A`가 성립합니다. 아래에 주어진 예를 참조하십시오.

`A`가 대칭인 경우, 즉 `HermOrSym{<:Real}` 유형인 경우 ([`eigen`](@ref))를 사용하여 세제곱근을 찾습니다. 그렇지 않으면, p-번째 근 알고리즘의 특수화된 버전 [^S03]이 사용되며, 이는 실수 값 슈르 분해 ([`schur`](@ref))를 활용하여 세제곱근을 계산합니다.

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# 예제

```jldoctest
julia> A = [0.927524 -0.15857; -1.3677 -1.01172]
2×2 Matrix{Float64}:
  0.927524  -0.15857
 -1.3677    -1.01172

julia> T = cbrt(A)
2×2 Matrix{Float64}:
  0.910077  -0.151019
 -1.30257   -0.936818

julia> T*T*T ≈ A
true
```
