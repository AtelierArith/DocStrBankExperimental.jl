```
cbrt(A::AbstractMatrix{<:Real})
```

Berechnet die reellwertige Kubikwurzel einer reellwertigen Matrix `A`. Wenn `T = cbrt(A)`, dann gilt `T*T*T ≈ A`, siehe das unten gegebene Beispiel.

Wenn `A` symmetrisch ist, d.h. vom Typ `HermOrSym{<:Real}`, dann wird ([`eigen`](@ref)) verwendet, um die Kubikwurzel zu finden. Andernfalls wird eine spezialisierte Version des p-ten Wurzelalgorithmus [^S03] verwendet, die die reellwertige Schur-Zerlegung ([`schur`](@ref)) nutzt, um die Kubikwurzel zu berechnen.

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# Beispiele

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
