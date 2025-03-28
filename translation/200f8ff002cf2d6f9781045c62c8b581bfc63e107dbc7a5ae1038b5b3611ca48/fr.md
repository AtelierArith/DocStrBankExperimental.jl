```
eigmin(A; permute::Bool=true, scale::Bool=true)
```

Retourne la plus petite valeur propre de `A`. L'option `permute=true` permute la matrice pour se rapprocher d'une forme triangulaire supérieure, et `scale=true` met à l'échelle la matrice par ses éléments diagonaux pour rendre les lignes et les colonnes plus égales en norme. Notez que si les valeurs propres de `A` sont complexes, cette méthode échouera, car les nombres complexes ne peuvent pas être triés.

# Exemples

```jldoctest
julia> A = [0 im; -im 0]
2×2 Matrix{Complex{Int64}}:
 0+0im  0+1im
 0-1im  0+0im

julia> eigmin(A)
-1.0

julia> A = [0 im; -1 0]
2×2 Matrix{Complex{Int64}}:
  0+0im  0+1im
 -1+0im  0+0im

julia> eigmin(A)
ERROR: DomainError with Complex{Int64}[0+0im 0+1im; -1+0im 0+0im]:
`A` ne peut pas avoir de valeurs propres complexes.
Stacktrace:
[...]
```
