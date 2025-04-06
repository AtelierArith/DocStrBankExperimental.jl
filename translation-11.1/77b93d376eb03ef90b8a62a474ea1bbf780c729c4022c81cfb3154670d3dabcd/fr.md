```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

Comme [`partialsortperm`](@ref), mais accepte un vecteur d'index préalloué `ix` de la même taille que `v`, qui est utilisé pour stocker (une permutation de) les indices de `v`.

`ix` est initialisé pour contenir les indices de `v`.

(En général, les indices de `v` seront `1:length(v)`, bien que si `v` a un type de tableau alternatif avec des indices non basés sur un, comme un `OffsetArray`, `ix` doit partager ces mêmes indices)

Au retour, `ix` est garanti d'avoir les indices `k` dans leurs positions triées, de sorte que

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

La valeur de retour est le `k`-ème élément de `ix` si `k` est un entier, ou une vue dans `ix` si `k` est une plage.

!!! avertissement
    Le comportement peut être inattendu lorsque tout argument muté partage de la mémoire avec un autre argument.


# Exemples

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
