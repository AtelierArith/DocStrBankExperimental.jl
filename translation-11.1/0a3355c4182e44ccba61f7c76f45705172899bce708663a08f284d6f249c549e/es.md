```
zip(iters...)
```

Ejecuta múltiples iteradores al mismo tiempo, hasta que cualquiera de ellos se agote. El tipo de valor del iterador `zip` es una tupla de valores de sus subiteradores.

!!! note
    `zip` ordena las llamadas a sus subiteradores de tal manera que los iteradores con estado no avanzarán cuando otro iterador termine en la iteración actual.


!!! note
    `zip()` sin argumentos produce un iterador infinito de tuplas vacías.


Véase también: [`enumerate`](@ref), [`Base.splat`](@ref).

# Ejemplos

```jldoctest
julia> a = 1:5
1:5

julia> b = ["e","d","b","c","a"]
5-element Vector{String}:
 "e"
 "d"
 "b"
 "c"
 "a"

julia> c = zip(a,b)
zip(1:5, ["e", "d", "b", "c", "a"])

julia> length(c)
5

julia> first(c)
(1, "e")
```
