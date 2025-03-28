```
IOBuffer(string::String)
```

Erstellen Sie einen schreibgeschützten `IOBuffer` für die Daten, die dem angegebenen String zugrunde liegen.

# Beispiele

```jldoctest
julia> io = IOBuffer("Haho");

julia> String(take!(io))
"Haho"

julia> String(take!(io))
"Haho"
```
