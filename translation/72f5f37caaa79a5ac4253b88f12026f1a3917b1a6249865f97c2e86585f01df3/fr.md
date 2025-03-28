```
StepRange{T, S} <: OrdinalRange{T, S}
```

Des plages avec des éléments de type `T` avec un espacement de type `S`. L'écart entre chaque élément est constant, et la plage est définie en termes d'un `start` et d'un `stop` de type `T` et d'un `step` de type `S`. Ni `T` ni `S` ne doivent être des types à virgule flottante. La syntaxe `a:b:c` avec `b != 0` et `a`, `b`, et `c` tous des entiers crée une `StepRange`.

# Exemples

```jldoctest
julia> collect(StepRange(1, Int8(2), 10))
5-element Vector{Int64}:
 1
 3
 5
 7
 9

julia> typeof(StepRange(1, Int8(2), 10))
StepRange{Int64, Int8}

julia> typeof(1:3:6)
StepRange{Int64, Int64}
```
