```
splitext(pfad::AbstractString) -> (String, String)
```

Wenn die letzte Komponente eines Pfades einen oder mehrere Punkte enthält, teile den Pfad in alles vor dem letzten Punkt und alles einschließlich und nach dem Punkt. Andernfalls gib ein Tupel des Arguments unverändert und den leeren String zurück. "splitext" ist die Abkürzung für "split extension".

# Beispiele

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
