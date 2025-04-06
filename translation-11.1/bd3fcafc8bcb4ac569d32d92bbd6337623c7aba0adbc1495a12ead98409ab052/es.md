```
Expr(head::Symbol, args...)
```

Un tipo que representa expresiones compuestas en código julia analizado (ASTs). Cada expresión consiste en un `head` `Symbol` que identifica qué tipo de expresión es (por ejemplo, una llamada, un bucle for, una declaración condicional, etc.), y subexpresiones (por ejemplo, los argumentos de una llamada). Las subexpresiones se almacenan en un campo `Vector{Any}` llamado `args`.

Consulta el capítulo del manual sobre [Metaprogramación](@ref) y la documentación para desarrolladores [Julia ASTs](@ref).

# Ejemplos

```jldoctest
julia> Expr(:call, :+, 1, 2)
:(1 + 2)

julia> dump(:(a ? b : c))
Expr
  head: Symbol if
  args: Array{Any}((3,))
    1: Symbol a
    2: Symbol b
    3: Symbol c
```
