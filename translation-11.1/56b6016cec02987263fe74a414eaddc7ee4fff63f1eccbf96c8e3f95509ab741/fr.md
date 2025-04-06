```
pop!(collection) -> item
```

Supprime un élément dans `collection` et le retourne. Si `collection` est un conteneur ordonné, le dernier élément est retourné ; pour les conteneurs non ordonnés, un élément arbitraire est retourné.

Voir aussi : [`popfirst!`](@ref), [`popat!`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`splice!`](@ref), et [`push!`](@ref).

# Exemples

```jldoctest
julia> A=[1, 2, 3]
3-element Vector{Int64}:
 1
 2
 3

julia> pop!(A)
3

julia> A
2-element Vector{Int64}:
 1
 2

julia> S = Set([1, 2])
Set{Int64} with 2 elements:
  2
  1

julia> pop!(S)
2

julia> S
Set{Int64} with 1 element:
  1

julia> pop!(Dict(1=>2))
1 => 2
```
