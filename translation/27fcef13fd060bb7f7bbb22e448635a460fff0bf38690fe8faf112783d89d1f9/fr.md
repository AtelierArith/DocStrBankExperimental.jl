```
Meta.quot(ex)::Expr
```

Citer l'expression `ex` pour produire une expression avec la tête `quote`. Cela peut par exemple être utilisé pour représenter des objets de type `Expr` dans l'AST. Voir aussi la section du manuel sur [QuoteNode](@ref man-quote-node).

# Exemples

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
