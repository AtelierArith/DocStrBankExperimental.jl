```
splitpath(path::AbstractString) -> Vector{String}
```

Divide una ruta de archivo en todos sus componentes de ruta. Esto es lo opuesto a `joinpath`. Devuelve un arreglo de subcadenas, una para cada directorio o archivo en la ruta, incluyendo el directorio raíz si está presente.

!!! compat "Julia 1.1"
    Esta función requiere al menos Julia 1.1.


# Ejemplos

```jldoctest
julia> splitpath("/home/myuser/example.jl")
4-element Vector{String}:
 "/"
 "home"
 "myuser"
 "example.jl"
```
