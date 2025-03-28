```
Meta.isexpr(ex, head[, n])::Bool
```

Retourne `true` si `ex` est un `Expr` avec le type donné `head` et éventuellement que la liste des arguments a une longueur de `n`. `head` peut être un `Symbol` ou une collection de `Symbol`s. Par exemple, pour vérifier qu'un macro a reçu une expression d'appel de fonction, vous pourriez utiliser `isexpr(ex, :call)`.

# Exemples

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # plusieurs têtes possibles
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
