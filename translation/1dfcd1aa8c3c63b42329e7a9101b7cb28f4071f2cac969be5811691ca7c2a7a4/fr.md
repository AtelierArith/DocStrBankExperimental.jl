```
popfirst!(collection) -> item
```

Supprime le premier `item` de `collection`.

Cette fonction s'appelle `shift` dans de nombreux autres langages de programmation.

Voir aussi : [`pop!`](@ref), [`popat!`](@ref), [`delete!`](@ref).

# Exemples

```jldoctest
julia> A = [1, 2, 3, 4, 5, 6]
6-element Vector{Int64}:
 1
 2
 3
 4
 5
 6

julia> popfirst!(A)
1

julia> A
5-element Vector{Int64}:
 2
 3
 4
 5
 6
```
