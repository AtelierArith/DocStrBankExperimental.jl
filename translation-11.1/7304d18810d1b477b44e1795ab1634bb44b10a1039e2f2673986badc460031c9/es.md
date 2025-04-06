```
Mmap.Anonymous(name::AbstractString="", readonly::Bool=false, create::Bool=true)
```

Crea un objeto similar a `IO` para crear memoria mapeada en cero que no está vinculada a un archivo para su uso en [`mmap`](@ref mmap). Utilizado por `SharedArray` para crear arreglos de memoria compartida.

# Ejemplos

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
