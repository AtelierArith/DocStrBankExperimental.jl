```
readuntil(stream::IO, delim; keep::Bool = false)
readuntil(filename::AbstractString, delim; keep::Bool = false)
```

Lee una cadena de un `stream` de E/S o de un archivo, hasta el delimitador dado. El delimitador puede ser un `UInt8`, `AbstractChar`, cadena o vector. El argumento clave `keep` controla si el delimitador se incluye en el resultado. Se asume que el texto está codificado en UTF-8.

Devuelve un `String` si `delim` es un `AbstractChar` o una cadena, o de lo contrario devuelve un `Vector{typeof(delim)}`. Véase también [`copyuntil`](@ref) para escribir en su lugar en otro stream (que puede ser un [`IOBuffer`](@ref) preasignado).

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> readuntil("my_file.txt", 'L')
"Julia"

julia> readuntil("my_file.txt", '.', keep = true)
"JuliaLang is a GitHub organization."

julia> rm("my_file.txt")
```
