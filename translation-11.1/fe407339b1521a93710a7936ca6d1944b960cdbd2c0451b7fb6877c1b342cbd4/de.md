```
isdir(pfad) -> Bool
```

Gibt `true` zurück, wenn `pfad` ein Verzeichnis ist, andernfalls `false`.

# Beispiele

```jldoctest
julia> isdir(homedir())
true

julia> isdir("not/a/directory")
false
```

Siehe auch [`isfile`](@ref) und [`ispath`](@ref).
