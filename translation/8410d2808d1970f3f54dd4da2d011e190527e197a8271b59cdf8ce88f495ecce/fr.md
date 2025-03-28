```
reduce(f, A::AbstractArray; dims=:, [init])
```

Réduit la fonction à 2 arguments `f` le long des dimensions de `A`. `dims` est un vecteur spécifiant les dimensions à réduire, et l'argument clé `init` est la valeur initiale à utiliser dans les réductions. Pour `+`, `*`, `max` et `min`, l'argument `init` est optionnel.

L'associativité de la réduction dépend de l'implémentation ; si vous avez besoin d'une associativité particulière, par exemple de gauche à droite, vous devriez écrire votre propre boucle ou envisager d'utiliser [`foldl`](@ref) ou [`foldr`](@ref). Voir la documentation pour [`reduce`](@ref).

# Exemples

```jldoctest
julia> a = reshape(Vector(1:16), (4,4))
4×4 Matrix{Int64}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> reduce(max, a, dims=2)
4×1 Matrix{Int64}:
 13
 14
 15
 16

julia> reduce(max, a, dims=1)
1×4 Matrix{Int64}:
 4  8  12  16
```
