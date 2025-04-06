```
Meta.quot(ex)::Expr
```

Zitat Ausdruck `ex`, um einen Ausdruck mit dem Kopf `quote` zu erzeugen. Dies kann beispielsweise verwendet werden, um Objekte vom Typ `Expr` im AST darzustellen. Siehe auch den Handbuchabschnitt über [QuoteNode](@ref man-quote-node).

# Beispiele

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
