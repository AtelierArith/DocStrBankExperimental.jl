```
qr!(A, pivot = NoPivot(); blocksize)
```

`qr!` est identique à [`qr`](@ref) lorsque `A` est un sous-type de [`AbstractMatrix`](@ref), mais économise de l'espace en écrasant l'entrée `A`, au lieu de créer une copie. Une exception [`InexactError`](@ref) est levée si la factorisation produit un nombre non représentable par le type d'élément de `A`, par exemple pour les types entiers.

!!! compat "Julia 1.4"
    L'argument clé `blocksize` nécessite Julia 1.4 ou une version ultérieure.


# Exemples

```jldoctest
julia> a = [1. 2.; 3. 4.]
2×2 Matrix{Float64}:
 1.0  2.0
 3.0  4.0

julia> qr!(a)
LinearAlgebra.QRCompactWY{Float64, Matrix{Float64}, Matrix{Float64}}
Facteur Q : 2×2 LinearAlgebra.QRCompactWYQ{Float64, Matrix{Float64}, Matrix{Float64}}
Facteur R :
2×2 Matrix{Float64}:
 -3.16228  -4.42719
  0.0      -0.632456

julia> a = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> qr!(a)
ERREUR : InexactError: Int64(3.1622776601683795)
Trace de la pile :
[...]
```
