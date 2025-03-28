```
get(collection, key, default)
```

Gibt den Wert zurück, der für den angegebenen Schlüssel gespeichert ist, oder den angegebenen Standardwert, wenn keine Zuordnung für den Schlüssel vorhanden ist.

!!! compat "Julia 1.7"
    Für Tupel und Zahlen erfordert diese Funktion mindestens Julia 1.7.


# Beispiele

```jldoctest
julia> d = Dict("a"=>1, "b"=>2);

julia> get(d, "a", 3)
1

julia> get(d, "c", 3)
3
```
