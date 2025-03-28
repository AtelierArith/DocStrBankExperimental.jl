```
Meta.quot(ex)::Expr
```

Cita la expresión `ex` para producir una expresión con cabeza `quote`. Esto se puede usar, por ejemplo, para representar objetos del tipo `Expr` en el AST. Consulta también la sección del manual sobre [QuoteNode](@ref man-quote-node).

# Ejemplos

```jldoctest
julia> eval(Meta.quot(:x))
:x

julia> dump(Meta.quot(:x))
Expr
  head: Symbol quote
  args: Array{Any}((1,))
    1: Symbol x

julia> eval(Meta.quot(:(1+2)))
:(1 + 2)
```
