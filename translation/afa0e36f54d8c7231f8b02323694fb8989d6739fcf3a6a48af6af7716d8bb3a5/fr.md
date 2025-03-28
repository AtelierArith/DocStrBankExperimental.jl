```
intersect(s, itrs...)
∩(s, itrs...)
```

Construit l'ensemble contenant les éléments qui apparaissent dans tous les arguments.

Le premier argument contrôle le type de conteneur qui est retourné. Si c'est un tableau, il maintient l'ordre dans lequel les éléments apparaissent pour la première fois.

Le symbole Unicode `∩` peut être tapé en écrivant `\cap` puis en appuyant sur tab dans le REPL Julia, et dans de nombreux éditeurs. C'est un opérateur infixe, permettant `s ∩ itr`.

Voir aussi [`setdiff`](@ref), [`isdisjoint`](@ref), [`issubset`](@ref Base.issubset), [`issetequal`](@ref).

!!! compat "Julia 1.8"
    À partir de Julia 1.8, intersect retourne un résultat avec le eltype des eltypes promus des deux entrées.


# Exemples

```jldoctest
julia> intersect([1, 2, 3], [3, 4, 5])
1-element Vector{Int64}:
 3

julia> intersect([1, 4, 4, 5, 6], [6, 4, 6, 7, 8])
2-element Vector{Int64}:
 4
 6

julia> intersect(1:16, 7:99)
7:16

julia> (0, 0.0) ∩ (-0.0, 0)
1-element Vector{Real}:
 0

julia> intersect(Set([1, 2]), BitSet([2, 3]), 1.0:10.0)
Set{Float64} with 1 element:
  2.0
```
