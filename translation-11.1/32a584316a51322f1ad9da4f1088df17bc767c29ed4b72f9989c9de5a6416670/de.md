```
get!(collection, key, default)
```

Gibt den Wert zurück, der für den angegebenen Schlüssel gespeichert ist, oder wenn keine Zuordnung für den Schlüssel vorhanden ist, speichere `key => default` und gebe `default` zurück.

# Beispiele

```jldoctest
julia> d = Dict("a"=>1, "b"=>2, "c"=>3);

julia> get!(d, "a", 5)
1

julia> get!(d, "d", 4)
4

julia> d
Dict{String, Int64} mit 4 Einträgen:
  "c" => 3
  "b" => 2
  "a" => 1
  "d" => 4
```
