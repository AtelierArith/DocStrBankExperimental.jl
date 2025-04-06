```
any(p, itr) -> Bool
```

Bestimmen Sie, ob das Prädikat `p` für irgendein Element von `itr` `true` zurückgibt, und geben Sie `true` zurück, sobald das erste Element in `itr` gefunden wird, für das `p` `true` zurückgibt (Short-Circuiting). Um bei `false` einen Short-Circuit zu machen, verwenden Sie [`all`](@ref).

Wenn die Eingabe [`missing`](@ref) Werte enthält, geben Sie `missing` zurück, wenn alle nicht fehlenden Werte `false` sind (oder äquivalent, wenn die Eingabe keinen `true` Wert enthält), gemäß der [dreiwertigen Logik](https://de.wikipedia.org/wiki/Dreiwertige_Logik).

# Beispiele

```jldoctest
julia> any(i->(4<=i<=6), [3,5,7])
true

julia> any(i -> (println(i); i > 3), 1:10)
1
2
3
4
true

julia> any(i -> i > 0, [1, missing])
true

julia> any(i -> i > 0, [-1, missing])
missing

julia> any(i -> i > 0, [-1, 0])
false
```
