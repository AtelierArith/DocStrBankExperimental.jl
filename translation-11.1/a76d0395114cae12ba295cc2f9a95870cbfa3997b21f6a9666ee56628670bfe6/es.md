```
:expr
```

Cita una expresión `expr`, devolviendo el árbol de sintaxis abstracta (AST) de `expr`. El AST puede ser de tipo `Expr`, `Symbol`, o un valor literal. La sintaxis `:identifier` se evalúa a un `Symbol`.

Ver también: [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# Ejemplos

```jldoctest
julia> expr = :(a = b + 2*x)
:(a = b + 2x)

julia> sym = :some_identifier
:some_identifier

julia> value = :0xff
0xff

julia> typeof((expr, sym, value))
Tuple{Expr, Symbol, UInt8}
```
