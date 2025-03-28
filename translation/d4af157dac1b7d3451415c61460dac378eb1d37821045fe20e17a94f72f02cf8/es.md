```
copyuntil(out::IO, stream::IO, delim; keep::Bool = false)
copyuntil(out::IO, filename::AbstractString, delim; keep::Bool = false)

Copia una cadena de un `stream` de I/O o de un archivo, hasta el delimitador dado, al stream `out`, devolviendo `out`. El delimitador puede ser un `UInt8`, `AbstractChar`, cadena o vector. El argumento clave `keep` controla si el delimitador se incluye en el resultado. Se asume que el texto está codificado en UTF-8.

Similar a [`readuntil`](@ref), que devuelve un `String`; en contraste, `copyuntil` escribe directamente en `out`, sin asignar una cadena. (Esto se puede usar, por ejemplo, para leer datos en un [`IOBuffer`](@ref) preasignado.)

# Ejemplos

```

jldoctest julia> write("my_file.txt", "JuliaLang is a GitHub organization.\nIt has many members.\n");

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", 'L'))) "Julia"

julia> String(take!(copyuntil(IOBuffer(), "my_file.txt", '.', keep = true))) "JuliaLang is a GitHub organization."

julia> rm("my_file.txt") ```
