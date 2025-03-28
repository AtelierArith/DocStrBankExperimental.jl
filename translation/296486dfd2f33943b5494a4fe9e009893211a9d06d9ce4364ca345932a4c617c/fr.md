```
LinearIndices(A::AbstractArray)
```

Retourne un tableau `LinearIndices` avec la même forme et les mêmes [`axes`](@ref) que `A`, contenant l'indice linéaire de chaque entrée dans `A`. L'indexation de ce tableau avec des indices cartésiens permet de les mapper à des indices linéaires.

Pour les tableaux avec une indexation conventionnelle (les indices commencent à 1), ou tout tableau multidimensionnel, les indices linéaires varient de 1 à `length(A)`. Cependant, pour les `AbstractVector`, les indices linéaires sont `axes(A, 1)`, et ne commencent donc pas à 1 pour les vecteurs avec une indexation non conventionnelle.

Appeler cette fonction est la manière "sûre" d'écrire des algorithmes qui exploitent l'indexation linéaire.

# Exemples

```jldoctest
julia> A = fill(1, (5,6,7));

julia> b = LinearIndices(A);

julia> extrema(b)
(1, 210)
```

```
LinearIndices(inds::CartesianIndices) -> R
LinearIndices(sz::Dims) -> R
LinearIndices((istart:istop, jstart:jstop, ...)) -> R
```

Retourne un tableau `LinearIndices` avec la forme spécifiée ou les [`axes`](@ref).

# Exemples

Le but principal de ce constructeur est la conversion intuitive de l'indexation cartésienne à l'indexation linéaire :

```jldoctest
julia> linear = LinearIndices((1:3, 1:2))
3×2 LinearIndices{2, Tuple{UnitRange{Int64}, UnitRange{Int64}}}:
 1  4
 2  5
 3  6

julia> linear[1,2]
4
```
