```
axes(A, d)
```

Renvoie la plage valide d'indices pour le tableau `A` le long de la dimension `d`.

Voir aussi [`size`](@ref), et le chapitre du manuel sur [les tableaux avec des indices personnalisés](@ref man-custom-indices).

# Exemples

```jldoctest
julia> A = fill(1, (5,6,7));

julia> axes(A, 2)
Base.OneTo(6)

julia> axes(A, 4) == 1:1  # toutes les dimensions d > ndims(A) ont une taille de 1
true
```

# Remarque d'utilisation

Chacun des indices doit être un `AbstractUnitRange{<:Integer}`, mais en même temps peut être un type qui utilise des indices personnalisés. Donc, par exemple, si vous avez besoin d'un sous-ensemble, utilisez des constructions d'indexation généralisées comme `begin`/`end` ou [`firstindex`](@ref)/[`lastindex`](@ref):

```julia
ix = axes(v, 1)
ix[2:end]          # fonctionnera par exemple pour Vector, mais peut échouer en général
ix[(begin+1):end]  # fonctionne pour des index généralisés
```
