```
splice!(a::Vector, indices, [replacement]) -> items
```

Supprime les éléments aux indices spécifiés et renvoie une collection contenant les éléments supprimés. Les éléments suivants sont décalés vers la gauche pour combler les espaces résultants. Si spécifié, les valeurs de remplacement d'une collection ordonnée seront insérées à la place des éléments supprimés ; dans ce cas, `indices` doit être un `AbstractUnitRange`.

Pour insérer `replacement` avant un index `n` sans supprimer d'éléments, utilisez `splice!(collection, n:n-1, replacement)`.

!!! warning
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


!!! compat "Julia 1.5"
    Avant Julia 1.5, `indices` devait toujours être un `UnitRange`.


!!! compat "Julia 1.8"
    Avant Julia 1.8, `indices` devait être un `UnitRange` si des valeurs de remplacement étaient insérées.


# Exemples

```jldoctest
julia> A = [-1, -2, -3, 5, 4, 3, -1]; splice!(A, 4:3, 2)
Int64[]

julia> A
8-element Vector{Int64}:
 -1
 -2
 -3
  2
  5
  4
  3
 -1
```
