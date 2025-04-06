```
union(s, itrs...)
∪(s, itrs...)
```

Construit un objet contenant tous les éléments distincts de tous les arguments.

Le premier argument contrôle le type de conteneur qui est retourné. Si c'est un tableau, il maintient l'ordre dans lequel les éléments apparaissent pour la première fois.

Le symbole Unicode `∪` peut être tapé en écrivant `\cup` puis en appuyant sur tab dans le REPL Julia, et dans de nombreux éditeurs. C'est un opérateur infixe, permettant `s ∪ itr`.

Voir aussi [`unique`](@ref), [`intersect`](@ref), [`isdisjoint`](@ref), [`vcat`](@ref), [`Iterators.flatten`](@ref).

# Exemples

```jldoctest
julia> union([1, 2], [3])
3-element Vector{Int64}:
 1
 2
 3

julia> union([4 2 3 4 4], 1:3, 3.0)
4-element Vector{Float64}:
 4.0
 2.0
 3.0
 1.0

julia> (0, 0.0) ∪ (-0.0, NaN)
3-element Vector{Real}:
   0
  -0.0
 NaN

julia> union(Set([1, 2]), 2:3)
Set{Int64} with 3 elements:
  2
  3
  1
```
