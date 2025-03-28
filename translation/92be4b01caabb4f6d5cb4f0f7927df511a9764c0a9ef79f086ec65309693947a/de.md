```
pop!(collection, key[, default])
```

Löschen und Rückgabe der Zuordnung für `key`, wenn sie in `collection` vorhanden ist, andernfalls Rückgabe von `default` oder Auslösen eines Fehlers, wenn `default` nicht angegeben ist.

# Beispiele

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> pop!(d, "a")
1

julia> pop!(d, "d")
ERROR: KeyError: key "d" not found
Stacktrace:
[...]

julia> pop!(d, "e", 4)
4
```
