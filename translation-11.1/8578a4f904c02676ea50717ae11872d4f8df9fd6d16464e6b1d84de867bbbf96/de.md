```
all(p, itr) -> Bool
```

Bestimmen Sie, ob das Prädikat `p` für alle Elemente von `itr` `true` zurückgibt, und geben Sie `false` zurück, sobald das erste Element in `itr` gefunden wird, für das `p` `false` zurückgibt (Short-Circuiting). Um bei `true` einen Short-Circuit zu machen, verwenden Sie [`any`](@ref).

Wenn die Eingabe [`missing`](@ref) Werte enthält, geben Sie `missing` zurück, wenn alle nicht fehlenden Werte `true` sind (oder äquivalent, wenn die Eingabe keinen `false` Wert enthält), gemäß der [dreiwertigen Logik](https://en.wikipedia.org/wiki/Three-valued_logic).

# Beispiele

```jldoctest
julia> all(i->(4<=i<=6), [4,5,6])
true

julia> all(i -> (println(i); i < 3), 1:10)
1
2
3
false

julia> all(i -> i > 0, [1, missing])
missing

julia> all(i -> i > 0, [-1, missing])
false

julia> all(i -> i > 0, [1, 2])
true
```
