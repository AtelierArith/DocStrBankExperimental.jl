```
isfile(pfad) -> Bool
```

Gibt `true` zurück, wenn `pfad` eine reguläre Datei ist, andernfalls `false`.

# Beispiele

```jldoctest
julia> isfile(homedir())
false

julia> dateiname = "test_file.txt";

julia> write(dateiname, "Hallo Welt!");

julia> isfile(dateiname)
true

julia> rm(dateiname);

julia> isfile(dateiname)
false
```

Siehe auch [`isdir`](@ref) und [`ispath`](@ref).
