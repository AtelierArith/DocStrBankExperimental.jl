```
cmp(x,y)
```

Gibt -1, 0 oder 1 zurück, je nachdem, ob `x` kleiner, gleich oder größer als `y` ist. Verwendet die totale Ordnung, die durch `isless` implementiert ist.

# Beispiele

```jldoctest
julia> cmp(1, 2)
-1

julia> cmp(2, 1)
1

julia> cmp(2+im, 3-im)
ERROR: MethodError: no method matching isless(::Complex{Int64}, ::Complex{Int64})
[...]
```
