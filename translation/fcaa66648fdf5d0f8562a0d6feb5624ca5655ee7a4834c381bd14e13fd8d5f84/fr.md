```
open(f::Function, args...; kwargs...)
```

Applique la fonction `f` au résultat de `open(args...; kwargs...)` et ferme le descripteur de fichier résultant à la fin.

# Exemples

```jldoctest
julia> write("myfile.txt", "Hello world!");

julia> open(io->read(io, String), "myfile.txt")
"Hello world!"

julia> rm("myfile.txt")
```
