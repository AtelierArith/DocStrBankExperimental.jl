```
:expr
```

Zitiert einen Ausdruck `expr` und gibt den abstrakten Syntaxbaum (AST) von `expr` zurück. Der AST kann vom Typ `Expr`, `Symbol` oder einem literalen Wert sein. Die Syntax `:identifier` wertet zu einem `Symbol` aus.

Siehe auch: [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# Beispiele

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
