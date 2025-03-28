```
collect(collection)
```

Devuelve un `Array` de todos los elementos en una colección o iterador. Para diccionarios, devuelve un `Vector` de `key=>value` [Pair](@ref Pair)s. Si el argumento es similar a un array o es un iterador con el rasgo [`HasShape`](@ref IteratorSize), el resultado tendrá la misma forma y número de dimensiones que el argumento.

Utilizado por [comprensiones](@ref man-comprehensions) para convertir una [expresión generadora](@ref man-generators) en un `Array`. Así, *en generadores*, se puede usar la notación de corchetes en lugar de llamar a `collect`, ver segundo ejemplo.

# Ejemplos

Recoger elementos de una colección `UnitRange{Int64}`:

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

Recoger elementos de un generador (mismo resultado que `[x^2 for x in 1:3]`):

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
