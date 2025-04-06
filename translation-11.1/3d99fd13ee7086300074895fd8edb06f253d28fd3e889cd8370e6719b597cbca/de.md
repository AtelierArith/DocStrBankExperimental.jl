```
splitdir(pfad::AbstractString) -> (AbstractString, AbstractString)
```

Teile einen Pfad in ein Tupel aus dem Verzeichnisnamen und dem Dateinamen.

# Beispiele

```jldoctest
julia> splitdir("/home/myuser")
("/home", "myuser")
```
