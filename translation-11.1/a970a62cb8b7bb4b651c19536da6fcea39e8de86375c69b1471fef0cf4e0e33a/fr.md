```
sum(f, A::AbstractArray; dims)
```

Somme des résultats de l'appel de la fonction `f` sur chaque élément d'un tableau sur les dimensions données.

# Exemples

```jldoctest
julia> A = [1 2; 3 4]
2×2 Matrix{Int64}:
 1  2
 3  4

julia> sum(abs2, A, dims=1)
1×2 Matrix{Int64}:
 10  20

julia> sum(abs2, A, dims=2)
2×1 Matrix{Int64}:
  5
 25
```
