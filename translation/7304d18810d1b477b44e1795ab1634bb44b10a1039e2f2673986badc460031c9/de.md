```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

Erstellt ein `IO`-ähnliches Objekt zum Erstellen von nullen-befülltem mmapped-Speicher, das nicht an eine Datei gebunden ist, zur Verwendung in [`mmap`](@ref mmap). Wird von `SharedArray` zum Erstellen von gemeinsam genutzten Speicherarrays verwendet.

# Beispiele

```jldoctest
julia> using Mmap

julia> anon = Mmap.Anonymous();

julia> isreadable(anon)
true

julia> iswritable(anon)
true

julia> isopen(anon)
true
```
