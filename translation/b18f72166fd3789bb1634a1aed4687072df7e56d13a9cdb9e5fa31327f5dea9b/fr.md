```
range(start, stop, length)
range(start, stop; length, step)
range(start; length, stop, step)
range(;start, length, stop, step)
```

Construisez un tableau spécialisé avec des éléments espacés uniformément et un stockage optimisé (un [`AbstractRange`](@ref)) à partir des arguments. Mathématiquement, une plage est déterminée de manière unique par n'importe quelle combinaison de trois des `start`, `step`, `stop` et `length`. Les invocations valides de range sont :

  * Appelez `range` avec n'importe quelle combinaison de trois des `start`, `step`, `stop`, `length`.
  * Appelez `range` avec deux des `start`, `stop`, `length`. Dans ce cas, `step` sera supposé être un. Si les deux arguments sont des entiers, un [`UnitRange`](@ref) sera retourné.
  * Appelez `range` avec un des `stop` ou `length`. `start` et `step` seront supposés être un.

Voir Aide Étendue pour des détails supplémentaires sur le type retourné. Voir aussi [`logrange`](@ref) pour des points espacés logarithmiquement.

# Exemples

```jldoctest
julia> range(1, length=100)
1:100

julia> range(1, stop=100)
1:100

julia> range(1, step=5, length=100)
1:5:496

julia> range(1, step=5, stop=100)
1:5:96

julia> range(1, 10, length=101)
1.0:0.09:10.0

julia> range(1, 100, step=5)
1:5:96

julia> range(stop=10, length=5)
6:10

julia> range(stop=10, step=1, length=5)
6:1:10

julia> range(start=1, step=1, stop=10)
1:1:10

julia> range(; length = 10)
Base.OneTo(10)

julia> range(; stop = 6)
Base.OneTo(6)

julia> range(; stop = 6.5)
1.0:1.0:6.0
```

Si `length` n'est pas spécifié et que `stop - start` n'est pas un multiple entier de `step`, une plage qui se termine avant `stop` sera produite.

```jldoctest
julia> range(1, 3.5, step=2)
1.0:2.0:3.0
```

Une attention particulière est accordée pour s'assurer que les valeurs intermédiaires sont calculées de manière rationnelle. Pour éviter cette surcharge induite, voir le constructeur [`LinRange`](@ref).

!!! compat "Julia 1.1"
    `stop` en tant qu'argument positionnel nécessite au moins Julia 1.1.


!!! compat "Julia 1.7"
    Les versions sans arguments de mot-clé et `start` en tant qu'argument de mot-clé nécessitent au moins Julia 1.7.


!!! compat "Julia 1.8"
    Les versions avec `stop` en tant qu'argument de mot-clé unique, ou `length` en tant qu'argument de mot-clé unique nécessitent au moins Julia 1.8.


# Aide Étendue

`range` produira un `Base.OneTo` lorsque les arguments sont des entiers et

  * Seul `length` est fourni
  * Seul `stop` est fourni

`range` produira un `UnitRange` lorsque les arguments sont des entiers et

  * Seuls `start` et `stop` sont fournis
  * Seuls `length` et `stop` sont fournis

Un `UnitRange` n'est pas produit si `step` est fourni même s'il est spécifié comme un.
