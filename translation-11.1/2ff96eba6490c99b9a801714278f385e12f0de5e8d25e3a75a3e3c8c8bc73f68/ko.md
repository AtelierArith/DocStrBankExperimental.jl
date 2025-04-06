```
pinv(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
pinv(M, rtol::Real) = pinv(M; rtol=rtol) # to be deprecated in Julia 2.0
```

Moore-Penrose 의사역행렬을 계산합니다.

부동 소수점 요소를 가진 행렬 `M`의 경우, `σ₁`이 `M`의 가장 큰 특이값일 때, `max(atol, rtol*σ₁)`보다 큰 특이값만 역전시켜 의사역행렬을 계산하는 것이 편리합니다.

절대 허용오차(`atol`)와 상대 허용오차(`rtol`)의 최적 선택은 `M`의 값과 의사역행렬의 의도된 응용에 따라 다릅니다. 기본 상대 허용오차는 `n*ϵ`이며, 여기서 `n`은 `M`의 가장 작은 차원의 크기이고, `ϵ`는 `M`의 요소 유형의 [`eps`](@ref)입니다.

밀집한 조건이 좋지 않은 행렬을 최소 제곱 방식으로 역전할 때는 `rtol = sqrt(eps(real(float(oneunit(eltype(M))))))`를 권장합니다.

자세한 내용은 [^issue8859], [^B96], [^S84], [^KY88]를 참조하십시오.

# 예제

```jldoctest
julia> M = [1.5 1.3; 1.2 1.9]
2×2 Matrix{Float64}:
 1.5  1.3
 1.2  1.9

julia> N = pinv(M)
2×2 Matrix{Float64}:
  1.47287   -1.00775
 -0.930233   1.16279

julia> M * N
2×2 Matrix{Float64}:
 1.0          -2.22045e-16
 4.44089e-16   1.0
```

[^issue8859]: Issue 8859, "Fix least squares", [https://github.com/JuliaLang/julia/pull/8859](https://github.com/JuliaLang/julia/pull/8859)

[^B96]: Åke Björck, "Numerical Methods for Least Squares Problems",  SIAM Press, Philadelphia, 1996, "Other Titles in Applied Mathematics", Vol. 51. [doi:10.1137/1.9781611971484](http://epubs.siam.org/doi/book/10.1137/1.9781611971484)

[^S84]: G. W. Stewart, "Rank Degeneracy", SIAM Journal on Scientific and Statistical Computing, 5(2), 1984, 403-413. [doi:10.1137/0905030](http://epubs.siam.org/doi/abs/10.1137/0905030)

[^KY88]: Konstantinos Konstantinides and Kung Yao, "Statistical analysis of effective singular values in matrix rank determination", IEEE Transactions on Acoustics, Speech and Signal Processing, 36(5), 1988, 757-763. [doi:10.1109/29.1585](https://doi.org/10.1109/29.1585)
