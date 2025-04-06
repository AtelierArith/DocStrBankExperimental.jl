```
diagm(v::AbstractVector)
diagm(m::Integer, n::Integer, v::AbstractVector)
```

Construit une matrice avec les éléments du vecteur comme éléments diagonaux. Par défaut, la matrice est carrée et sa taille est donnée par `length(v)`, mais une taille non carrée `m`×`n` peut être spécifiée en passant `m,n` comme premiers arguments.

# Exemples

```jldoctest
julia> diagm([1,2,3])
3×3 Matrix{Int64}:
 1  0  0
 0  2  0
 0  0  3
```
