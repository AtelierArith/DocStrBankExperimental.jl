```
:expr
```

Citez une expression `expr`, retournant l'arbre de syntaxe abstraite (AST) de `expr`. L'AST peut être de type `Expr`, `Symbol`, ou une valeur littérale. La syntaxe `:identifier` évalue à un `Symbol`.

Voir aussi : [`Expr`](@ref), [`Symbol`](@ref), [`Meta.parse`](@ref)

# Exemples

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
