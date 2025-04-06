```
pinv(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
pinv(M, rtol::Real) = pinv(M; rtol=rtol) # 在 Julia 2.0 中将被弃用
```

计算摩尔-彭若斯伪逆。

对于具有浮点元素的矩阵 `M`，通过仅反转大于 `max(atol, rtol*σ₁)` 的奇异值来计算伪逆是方便的，其中 `σ₁` 是 `M` 的最大奇异值。

绝对容忍度（`atol`）和相对容忍度（`rtol`）的最佳选择因 `M` 的值和伪逆的预期应用而异。默认的相对容忍度是 `n*ϵ`，其中 `n` 是 `M` 最小维度的大小，`ϵ` 是 `M` 元素类型的 [`eps`](@ref)。

对于以最小二乘意义反转稠密病态矩阵，建议使用 `rtol = sqrt(eps(real(float(oneunit(eltype(M))))))`。

有关更多信息，请参见 [^issue8859], [^B96], [^S84], [^KY88]。

# 示例

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

[^KY88]: Konstantinos Konstantinides 和 Kung Yao, "Statistical analysis of effective singular values in matrix rank determination", IEEE Transactions on Acoustics, Speech and Signal Processing, 36(5), 1988, 757-763. [doi:10.1109/29.1585](https://doi.org/10.1109/29.1585)
