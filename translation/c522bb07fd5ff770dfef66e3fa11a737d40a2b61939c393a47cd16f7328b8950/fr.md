```
one(x)
one(T::type)
```

Retourne une identité multiplicative pour `x` : une valeur telle que `one(x)*x == x*one(x) == x`. Alternativement, `one(T)` peut prendre un type `T`, auquel cas `one` retourne une identité multiplicative pour tout `x` de type `T`.

Si possible, `one(x)` retourne une valeur du même type que `x`, et `one(T)` retourne une valeur de type `T`. Cependant, cela peut ne pas être le cas pour les types représentant des quantités dimensionnelles (par exemple, le temps en jours), puisque l'identité multiplicative doit être sans dimension. Dans ce cas, `one(x)` devrait retourner une valeur d'identité de la même précision (et forme, pour les matrices) que `x`.

Si vous voulez une quantité qui est du même type que `x`, ou de type `T`, même si `x` est dimensionnelle, utilisez [`oneunit`](@ref) à la place.

Voir aussi la fonction [`identity`](@ref), et `I` dans [`LinearAlgebra`](@ref man-linalg) pour la matrice identité.

# Exemples

```jldoctest
julia> one(3.7)
1.0

julia> one(Int)
1

julia> import Dates; one(Dates.Day(1))
1
```
