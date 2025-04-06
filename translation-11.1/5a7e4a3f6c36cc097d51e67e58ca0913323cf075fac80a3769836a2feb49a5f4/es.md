```
cbrt(A::AbstractMatrix{<:Real})
```

Calcula la raíz cúbica de valor real de una matriz de valor real `A`. Si `T = cbrt(A)`, entonces tenemos `T*T*T ≈ A`, ver el ejemplo dado a continuación.

Si `A` es simétrica, es decir, de tipo `HermOrSym{<:Real}`, entonces se utiliza ([`eigen`](@ref)) para encontrar la raíz cúbica. De lo contrario, se utiliza una versión especializada del algoritmo de raíz p-ésima [^S03], que explota la descomposición de Schur de valor real ([`schur`](@ref)) para calcular la raíz cúbica.

[^S03]: Matthew I. Smith, "A Schur Algorithm for Computing Matrix pth Roots", SIAM Journal on Matrix Analysis and Applications, vol. 24, 2003, pp. 971–989. [doi:10.1137/S0895479801392697](https://doi.org/10.1137/s0895479801392697)

# Ejemplos

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
