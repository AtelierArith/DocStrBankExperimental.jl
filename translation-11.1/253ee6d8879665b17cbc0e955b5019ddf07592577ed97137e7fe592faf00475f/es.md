```
readlines(io::IO=stdin; keep::Bool=false)
readlines(filename::AbstractString; keep::Bool=false)
```

Lee todas las líneas de un flujo de I/O o de un archivo como un vector de cadenas. El comportamiento es equivalente a guardar el resultado de leer [`readline`](@ref) repetidamente con los mismos argumentos y guardar las líneas resultantes como un vector de cadenas. Véase también [`eachline`](@ref) para iterar sobre las líneas sin leerlas todas a la vez.

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readlines("my_file.txt")
2-element Vector{String}:
 "JuliaLang is a GitHub organization."
 "It has many members."

julia> readlines("my_file.txt", keep=true)
2-element Vector{String}:
 "JuliaLang is a GitHub organization.\n"
 "It has many members.\n"

julia> rm("my_file.txt")
```
