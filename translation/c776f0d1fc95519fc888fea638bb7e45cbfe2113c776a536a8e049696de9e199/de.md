```
isabstracttype(T)
```

Bestimmen Sie, ob der Typ `T` als abstrakter Typ deklariert wurde (d.h. unter Verwendung der `abstract type`-Syntax). Beachten Sie, dass dies nicht die Negation von `isconcretetype(T)` ist. Wenn `T` kein Typ ist, geben Sie `false` zurück.

# Beispiele

```jldoctest
julia> isabstracttype(AbstractArray)
true

julia> isabstracttype(Vector)
false
```
