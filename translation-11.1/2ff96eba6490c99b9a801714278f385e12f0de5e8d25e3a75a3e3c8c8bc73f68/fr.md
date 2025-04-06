```
pinv(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
pinv(M, rtol::Real) = pinv(M; rtol=rtol) # à déprécier dans Julia 2.0
```

Calcule la pseudo-inverse de Moore-Penrose.

Pour les matrices `M` avec des éléments à virgule flottante, il est pratique de calculer la pseudo-inverse en inversant uniquement les valeurs singulières supérieures à `max(atol, rtol*σ₁)` où `σ₁` est la plus grande valeur singulière de `M`.

Le choix optimal de la tolérance absolue (`atol`) et de la tolérance relative (`rtol`) varie à la fois avec la valeur de `M` et l'application prévue de la pseudo-inverse. La tolérance relative par défaut est `n*ϵ`, où `n` est la taille de la plus petite dimension de `M`, et `ϵ` est le [`eps`](@ref) du type d'élément de `M`.

Pour inverser des matrices denses mal conditionnées dans un sens des moindres carrés, `rtol = sqrt(eps(real(float(oneunit(eltype(M))))))` est recommandé.

Pour plus d'informations, voir [^issue8859], [^B96], [^S84], [^KY88].

# Exemples

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

[^KY88]: Konstantinos Konstantinides et Kung Yao, "Statistical analysis of effective singular values in matrix rank determination", IEEE Transactions on Acoustics, Speech and Signal Processing, 36(5), 1988, 757-763. [doi:10.1109/29.1585](https://doi.org/10.1109/29.1585)
