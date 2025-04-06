```
isdirpath(path::AbstractString) -> Bool
```

Bestimmen Sie, ob ein Pfad auf ein Verzeichnis verweist (zum Beispiel, ob er mit einem Pfadtrennzeichen endet).

# Beispiele

```jldoctest
julia> isdirpath("/home")
false

julia> isdirpath("/home/")
true
```
