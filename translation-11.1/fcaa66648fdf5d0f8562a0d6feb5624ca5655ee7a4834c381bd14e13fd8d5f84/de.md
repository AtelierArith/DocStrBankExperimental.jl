```
open(f::Function, args...; kwargs...)
```

Wenden Sie die Funktion `f` auf das Ergebnis von `open(args...; kwargs...)` an und schließen Sie den resultierenden Dateideskriptor nach Abschluss.

# Beispiele

```jldoctest
julia> write("myfile.txt", "Hello world!");

julia> open(io->read(io, String), "myfile.txt")
"Hello world!"

julia> rm("myfile.txt")
```
