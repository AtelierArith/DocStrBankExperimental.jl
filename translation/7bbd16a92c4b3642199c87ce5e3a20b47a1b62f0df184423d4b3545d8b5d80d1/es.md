```
sprint(f::Function, args...; context=nothing, sizehint=0)
```

Llama a la función dada con un flujo de I/O y los argumentos adicionales suministrados. Todo lo escrito en este flujo de I/O se devuelve como una cadena. `context` puede ser un [`IOContext`](@ref) cuyas propiedades se utilizarán, un `Pair` que especifica una propiedad y su valor, o una tupla de `Pair` que especifica múltiples propiedades y sus valores. `sizehint` sugiere la capacidad del búfer (en bytes).

El argumento opcional `context` puede establecerse en un par `:key=>value`, una tupla de pares `:key=>value`, o un objeto `IO` o [`IOContext`](@ref) cuyas atributos se utilizan para el flujo de I/O pasado a `f`. El opcional `sizehint` es un tamaño sugerido (en bytes) para asignar al búfer utilizado para escribir la cadena.

!!! compat "Julia 1.7"
    Pasar una tupla al argumento clave `context` requiere Julia 1.7 o posterior.


# Ejemplos

```jldoctest
julia> sprint(show, 66.66666; context=:compact => true)
"66.6667"

julia> sprint(showerror, BoundsError([1], 100))
"BoundsError: attempt to access 1-element Vector{Int64} at index [100]"
```
