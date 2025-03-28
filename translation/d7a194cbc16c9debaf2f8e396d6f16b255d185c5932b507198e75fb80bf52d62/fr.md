```
collect(collection)
```

Renvoie un `Array` de tous les éléments d'une collection ou d'un itérateur. Pour les dictionnaires, renvoie un `Vector` de `key=>value` [Pair](@ref Pair)s. Si l'argument est de type tableau ou est un itérateur avec le trait [`HasShape`](@ref IteratorSize), le résultat aura la même forme et le même nombre de dimensions que l'argument.

Utilisé par [les compréhensions](@ref man-comprehensions) pour transformer une [expression génératrice](@ref man-generators) en un `Array`. Ainsi, *sur les générateurs*, la notation entre crochets peut être utilisée au lieu d'appeler `collect`, voir le deuxième exemple.

# Exemples

Collecter des éléments d'une collection `UnitRange{Int64}` :

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

Collecter des éléments d'un générateur (même sortie que `[x^2 for x in 1:3]`) :

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
