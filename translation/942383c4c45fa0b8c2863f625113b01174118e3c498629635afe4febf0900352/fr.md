```
LU <: Factorization
```

Type de factorisation matricielle de la factorisation `LU` d'une matrice carrée `A`. C'est le type de retour de [`lu`](@ref), la fonction de factorisation matricielle correspondante.

Les composants individuels de la factorisation `F::LU` peuvent être accédés via [`getproperty`](@ref):

| Composant | Description                                           |
|:--------- |:----------------------------------------------------- |
| `F.L`     | partie `L` (triangulaire inférieure unitaire) de `LU` |
| `F.U`     | partie `U` (triangulaire supérieure) de `LU`          |
| `F.p`     | permutation `Vector` (droite)                         |
| `F.P`     | permutation `Matrix` (droite)                         |

L'itération sur la factorisation produit les composants `F.L`, `F.U` et `F.p`.

# Exemples

```jldoctest
julia> A = [4 3; 6 3]
2×2 Matrix{Int64}:
 4  3
 6  3

julia> F = lu(A)
LU{Float64, Matrix{Float64}, Vector{Int64}}
L facteur:
2×2 Matrix{Float64}:
 1.0       0.0
 0.666667  1.0
U facteur:
2×2 Matrix{Float64}:
 6.0  3.0
 0.0  1.0

julia> F.L * F.U == A[F.p, :]
true

julia> l, u, p = lu(A); # déstructuration via itération

julia> l == F.L && u == F.U && p == F.p
true
```
