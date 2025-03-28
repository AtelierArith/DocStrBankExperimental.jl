```
mod2pi(x)
```

Modulus après division par `2π`, retournant dans l'intervalle $[0,2π)$.

Cette fonction calcule une représentation en virgule flottante du modulus après division par `2π` numériquement exact, et n'est donc pas exactement la même que `mod(x,2π)`, qui calculerait le modulus de `x` par rapport à la division par le nombre en virgule flottante `2π`.

!!! note
    En fonction du format de la valeur d'entrée, la valeur représentable la plus proche de 2π peut être inférieure à 2π. Par exemple, l'expression `mod2pi(2π)` ne retournera pas `0`, car la valeur intermédiaire de `2*π` est un `Float64` et `2*Float64(π) < 2*big(π)`. Voir [`rem2pi`](@ref) pour un contrôle plus raffiné de ce comportement.


# Exemples

```jldoctest
julia> mod2pi(9*pi/4)
0.7853981633974481
```
