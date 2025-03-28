```
Meta.isexpr(ex, head[, n])::Bool
```

Gibt `true` zurück, wenn `ex` ein `Expr` mit dem gegebenen Typ `head` ist und optional, dass die Argumentliste die Länge `n` hat. `head` kann ein `Symbol` oder eine Sammlung von `Symbol`s sein. Zum Beispiel, um zu überprüfen, ob ein Makro einen Funktionsaufrufausdruck übergeben wurde, könnten Sie `isexpr(ex, :call)` verwenden.

# Beispiele

```jldoctest
julia> ex = :(f(x))
:(f(x))

julia> Meta.isexpr(ex, :block)
false

julia> Meta.isexpr(ex, :call)
true

julia> Meta.isexpr(ex, [:block, :call]) # mehrere mögliche Köpfe
true

julia> Meta.isexpr(ex, :call, 1)
false

julia> Meta.isexpr(ex, :call, 2)
true
```
