```
splitext(path::AbstractString) -> (String, String)
```

Si el último componente de una ruta contiene uno o más puntos, divide la ruta en todo lo que está antes del último punto y todo lo que incluye y después del punto. De lo contrario, devuelve una tupla del argumento sin modificar y la cadena vacía. "splitext" es una abreviatura de "dividir extensión".

# Ejemplos

```jldoctest
julia> splitext("/home/myuser/example.jl")
("/home/myuser/example", ".jl")

julia> splitext("/home/myuser/example.tar.gz")
("/home/myuser/example.tar", ".gz")

julia> splitext("/home/my.user/example")
("/home/my.user/example", "")
```
