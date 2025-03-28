```
struct
```

Le type le plus couramment utilisé en Julia est un struct, spécifié par un nom et un ensemble de champs.

```julia
struct Point
    x
    y
end
```

Les champs peuvent avoir des restrictions de type, qui peuvent être paramétrées :

```julia
struct Point{X}
    x::X
    y::Float64
end
```

Un struct peut également déclarer un super type abstrait via la syntaxe `<:` :

```julia
struct Point <: AbstractPoint
    x
    y
end
```

Les `struct`s sont immuables par défaut ; une instance de l'un de ces types ne peut pas être modifiée après sa construction. Utilisez [`mutable struct`](@ref) à la place pour déclarer un type dont les instances peuvent être modifiées.

Voir la section du manuel sur [Composite Types](@ref) pour plus de détails, comme la façon de définir des constructeurs.
