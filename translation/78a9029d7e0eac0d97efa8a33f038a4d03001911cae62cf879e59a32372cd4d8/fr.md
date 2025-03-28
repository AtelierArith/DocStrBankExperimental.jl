```
factoriser(A)
```

Calcule une factorisation pratique de `A`, basée sur le type de la matrice d'entrée. `factoriser` vérifie `A` pour voir si elle est symétrique/triangulaire/etc. si `A` est passée comme une matrice générique. `factoriser` vérifie chaque élément de `A` pour vérifier/réfuter chaque propriété. Elle s'arrêtera dès qu'elle pourra exclure la symétrie/la structure triangulaire. La valeur de retour peut être réutilisée pour résoudre efficacement plusieurs systèmes. Par exemple : `A=factoriser(A); x=A\b; y=A\C`.

| Propriétés de `A`              | type de factorisation                       |
|:------------------------------ |:------------------------------------------- |
| Positive définie               | Cholesky (voir [`cholesky`](@ref))          |
| Dense Symétrique/Hermitien     | Bunch-Kaufman (voir [`bunchkaufman`](@ref)) |
| Sparse Symétrique/Hermitien    | LDLt (voir [`ldlt`](@ref))                  |
| Triangulaire                   | Triangulaire                                |
| Diagonale                      | Diagonale                                   |
| Bidiagonale                    | Bidiagonale                                 |
| Tridiagonale                   | LU (voir [`lu`](@ref))                      |
| Tridiagonale réelle symétrique | LDLt (voir [`ldlt`](@ref))                  |
| Carrée générale                | LU (voir [`lu`](@ref))                      |
| Non carrée générale            | QR (voir [`qr`](@ref))                      |

Si `factoriser` est appelé sur une matrice hermitienne positive définie, par exemple, alors `factoriser` renverra une factorisation de Cholesky.

# Exemples

```jldoctest
julia> A = Array(Bidiagonal(fill(1.0, (5, 5)), :U))
5×5 Matrix{Float64}:
 1.0  1.0  0.0  0.0  0.0
 0.0  1.0  1.0  0.0  0.0
 0.0  0.0  1.0  1.0  0.0
 0.0  0.0  0.0  1.0  1.0
 0.0  0.0  0.0  0.0  1.0

julia> factoriser(A) # factoriser vérifiera si A est déjà factorisée
5×5 Bidiagonal{Float64, Vector{Float64}}:
 1.0  1.0   ⋅    ⋅    ⋅
  ⋅   1.0  1.0   ⋅    ⋅
  ⋅    ⋅   1.0  1.0   ⋅
  ⋅    ⋅    ⋅   1.0  1.0
  ⋅    ⋅    ⋅    ⋅   1.0
```

Cela renvoie un `5×5 Bidiagonal{Float64}`, qui peut maintenant être passé à d'autres fonctions d'algèbre linéaire (par exemple, des solveurs d'autovalues) qui utiliseront des méthodes spécialisées pour les types `Bidiagonal`.
