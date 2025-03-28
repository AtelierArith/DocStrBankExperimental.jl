```
collect(collection)
```

Gibt ein `Array` aller Elemente in einer Sammlung oder einem Iterator zurück. Für Wörterbücher wird ein `Vector` von `key=>value` [Pair](@ref Pair)s zurückgegeben. Wenn das Argument array-ähnlich ist oder ein Iterator mit dem [`HasShape`](@ref IteratorSize) Trait ist, hat das Ergebnis die gleiche Form und Anzahl der Dimensionen wie das Argument.

Wird von [Komprehensionen](@ref man-comprehensions) verwendet, um einen [Generatorausdruck](@ref man-generators) in ein `Array` umzuwandeln. Daher kann *bei Generatoren* die eckige Klammernotation anstelle des Aufrufs von `collect` verwendet werden, siehe zweites Beispiel.

# Beispiele

Sammeln von Elementen aus einer `UnitRange{Int64}`-Sammlung:

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

Sammeln von Elementen aus einem Generator (gleiche Ausgabe wie `[x^2 for x in 1:3]`):

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
