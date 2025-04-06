```
copyline(out::IO, io::IO=stdin; keep::Bool=false)
copyline(out::IO, filename::AbstractString; keep::Bool=false)
```

Copia una sola línea de texto de un `stream` de I/O o de un archivo al `stream` de `out`, devolviendo `out`.

Al leer de un archivo, se asume que el texto está codificado en UTF-8. Las líneas en la entrada terminan con `'\n'` o `"\r\n"` o el final de un stream de entrada. Cuando `keep` es falso (como lo es por defecto), estos caracteres de nueva línea al final se eliminan de la línea antes de que se devuelva. Cuando `keep` es verdadero, se devuelven como parte de la línea.

Similar a [`readline`](@ref), que devuelve un `String`; en contraste, `copyline` escribe directamente en `out`, sin asignar una cadena. (Esto se puede usar, por ejemplo, para leer datos en un [`IOBuffer`](@ref) preasignado.)

Consulta también [`copyuntil`](@ref) para leer hasta delimitadores más generales.

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang es una organización de GitHub.\nTiene muchos miembros.\n");

julia> String(take!(copyline(IOBuffer(), "my_file.txt")))
"JuliaLang es una organización de GitHub."

julia> String(take!(copyline(IOBuffer(), "my_file.txt", keep=true)))
"JuliaLang es una organización de GitHub.\n"

julia> rm("my_file.txt")
```
