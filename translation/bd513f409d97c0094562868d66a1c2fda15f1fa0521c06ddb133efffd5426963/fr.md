```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

Supprime l'élément à l'index donné et retourne l'élément supprimé. Les éléments suivants sont décalés vers la gauche pour combler le vide résultant. Si spécifié, les valeurs de remplacement d'une collection ordonnée seront insérées à la place de l'élément supprimé.

Voir aussi : [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref).

# Exemples

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

Pour insérer `replacement` avant un index `n` sans supprimer d'éléments, utilisez `splice!(collection, n:n-1, replacement)`.
