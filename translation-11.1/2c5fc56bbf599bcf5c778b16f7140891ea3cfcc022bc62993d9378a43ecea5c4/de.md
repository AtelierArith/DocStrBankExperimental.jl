```
delete!(collection, key)
```

Löschen Sie die Zuordnung für den angegebenen Schlüssel in einer Sammlung, falls vorhanden, und geben Sie die Sammlung zurück.

# Beispiele

```jldoctest
julia> d = Dict("a"=>1, "b"=>2)
Dict{String, Int64} mit 2 Einträgen:
  "b" => 2
  "a" => 1

julia> delete!(d, "b")
Dict{String, Int64} mit 1 Eintrag:
  "a" => 1

julia> delete!(d, "b") # d bleibt unverändert
Dict{String, Int64} mit 1 Eintrag:
  "a" => 1
```
