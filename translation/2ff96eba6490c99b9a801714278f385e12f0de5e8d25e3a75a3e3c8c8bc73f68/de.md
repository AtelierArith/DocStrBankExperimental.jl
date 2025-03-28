```
pinv(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
pinv(M, rtol::Real) = pinv(M; rtol=rtol) # wird in Julia 2.0 veraltet sein
```

Berechnet die Moore-Penrose-Pseudoinverse.

Für Matrizen `M` mit Gleitkommaelementen ist es praktisch, die Pseudoinverse zu berechnen, indem nur singuläre Werte größer als `max(atol, rtol*σ₁)` invertiert werden, wobei `σ₁` der größte singuläre Wert von `M` ist.

Die optimale Wahl der absoluten (`atol`) und relativen Toleranz (`rtol`) variiert sowohl mit dem Wert von `M` als auch mit der beabsichtigten Anwendung der Pseudoinverse. Die standardmäßige relative Toleranz ist `n*ϵ`, wobei `n` die Größe der kleinsten Dimension von `M` ist und `ϵ` die [`eps`](@ref) des Elementtyps von `M` ist.

Für die Inversion dichter, schlecht konditionierter Matrizen im Sinne der kleinsten Quadrate wird `rtol = sqrt(eps(real(float(oneunit(eltype(M))))))` empfohlen.

Für weitere Informationen siehe [^issue8859], [^B96], [^S84], [^KY88].

# Beispiele

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

[^KY88]: Konstantinos Konstantinides und Kung Yao, "Statistical analysis of effective singular values in matrix rank determination", IEEE Transactions on Acoustics, Speech and Signal Processing, 36(5), 1988, 757-763. [doi:10.1109/29.1585](https://doi.org/10.1109/29.1585)
