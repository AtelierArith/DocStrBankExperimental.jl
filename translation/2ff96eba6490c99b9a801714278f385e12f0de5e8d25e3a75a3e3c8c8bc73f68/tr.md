```
pinv(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
pinv(M, rtol::Real) = pinv(M; rtol=rtol) # to be deprecated in Julia 2.0
```

Moore-Penrose pseudoinversini hesaplar.

`M` matrisleri için, kayan nokta elemanları ile, pseudoinversi yalnızca `max(atol, rtol*σ₁)` değerinden büyük olan tekil değerleri ters çevirerek hesaplamak uygundur; burada `σ₁`, `M`'nin en büyük tekil değeridir.

Kesinlik (`atol`) ve göreceli tolerans (`rtol`) için en iyi seçim, hem `M`'nin değeri hem de pseudoinversin amaçlanan uygulaması ile değişir. Varsayılan göreceli tolerans `n*ϵ`'dir; burada `n`, `M`'nin en küçük boyutunun boyutudur ve `ϵ`, `M`'nin eleman türünün [`eps`](@ref) değeridir.

Yoğun, kötü koşullu matrisleri en küçük kareler anlamında ters çevirmek için `rtol = sqrt(eps(real(float(oneunit(eltype(M))))))` önerilir.

Daha fazla bilgi için bkz. [^issue8859], [^B96], [^S84], [^KY88].

# Örnekler

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

[^KY88]: Konstantinos Konstantinides ve Kung Yao, "Statistical analysis of effective singular values in matrix rank determination", IEEE Transactions on Acoustics, Speech and Signal Processing, 36(5), 1988, 757-763. [doi:10.1109/29.1585](https://doi.org/10.1109/29.1585)
