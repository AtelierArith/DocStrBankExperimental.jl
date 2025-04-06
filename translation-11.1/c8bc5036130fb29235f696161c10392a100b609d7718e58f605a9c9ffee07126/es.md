```
Meta.isexpr(ex, head[, n])::Bool
```

Devuelve `true` si `ex` es un `Expr` con el tipo dado `head` y opcionalmente que la lista de argumentos tiene una longitud de `n`. `head` puede ser un `Symbol` o una colección de `Symbol`s. Por ejemplo, para verificar que a una macro se le pasó una expresión de llamada a función, podrías usar `isexpr(ex, :call)`.

# Ejemplos

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # múltiples cabezas posibles
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
