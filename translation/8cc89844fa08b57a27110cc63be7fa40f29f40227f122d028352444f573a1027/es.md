```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

Determina si la función genérica dada tiene un método que coincide con el `Tuple` de tipos de argumento dados con el límite superior de la edad del mundo dado por `world`.

Si se proporciona un tuple de nombres de argumentos clave `kwnames`, esto también verifica si el método de `f` que coincide con `t` tiene los nombres de argumentos clave dados. Si el método coincidente acepta un número variable de argumentos clave, por ejemplo, con `kwargs...`, cualquier nombre dado en `kwnames` se considera válido. De lo contrario, los nombres proporcionados deben ser un subconjunto de los argumentos clave del método.

Véase también [`applicable`](@ref).

!!! compat "Julia 1.2"
    Proporcionar nombres de argumentos clave requiere Julia 1.2 o posterior.


# Ejemplos

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g acepta kwargs arbitrarios
true
```
