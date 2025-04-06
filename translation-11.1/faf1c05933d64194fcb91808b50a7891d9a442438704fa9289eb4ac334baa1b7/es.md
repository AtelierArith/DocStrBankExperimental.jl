```
readline(io::IO=stdin; keep::Bool=false)
readline(filename::AbstractString; keep::Bool=false)
```

Lee una sola línea de texto del flujo de I/O o archivo dado (por defecto es `stdin`). Al leer de un archivo, se asume que el texto está codificado en UTF-8. Las líneas en la entrada terminan con `'\n'` o `"\r\n"` o el final de un flujo de entrada. Cuando `keep` es falso (como lo es por defecto), estos caracteres de nueva línea al final se eliminan de la línea antes de que se devuelva. Cuando `keep` es verdadero, se devuelven como parte de la línea.

Devuelve un `String`.   Véase también [`copyline`](@ref) para escribir en su lugar en otro flujo (que puede ser un [`IOBuffer`](@ref) preasignado).

Véase también [`readuntil`](@ref) para leer hasta delimitadores más generales.

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang es una organización de GitHub.\nTiene muchos miembros.\n");

julia> readline("my_file.txt")
"JuliaLang es una organización de GitHub."

julia> readline("my_file.txt", keep=true)
"JuliaLang es una organización de GitHub.\n"

julia> rm("my_file.txt")
```

```julia-repl
julia> print("Introduce tu nombre: ")
Introduce tu nombre:

julia> your_name = readline()
Logan
"Logan"
```
