```
dirname(path::AbstractString) -> String
```

Holen Sie den Verzeichnisteil eines Pfades. Nachfolgende Zeichen ('/' oder '\') im Pfad werden als Teil des Pfades gezählt.

# Beispiele

```jldoctest
julia> dirname("/home/myuser")
"/home"

julia> dirname("/home/myuser/")
"/home/myuser"
```

Siehe auch [`basename`](@ref).
