```
eachline(io::IO=stdin; keep::Bool=false)
eachline(filename::AbstractString; keep::Bool=false)
```

Crea un objeto iterable `EachLine` que generará cada línea de un flujo de E/S o un archivo. La iteración llama a [`readline`](@ref) en el argumento de flujo repetidamente con `keep` pasado, determinando si se retienen los caracteres de fin de línea al final. Cuando se llama con un nombre de archivo, el archivo se abre una vez al comienzo de la iteración y se cierra al final. Si la iteración se interrumpe, el archivo se cerrará cuando el objeto `EachLine` sea recolectado por el garbage collector.

Para iterar sobre cada línea de un `String`, se puede usar `eachline(IOBuffer(str))`.

[`Iterators.reverse`](@ref) se puede usar en un objeto `EachLine` para leer las líneas en orden inverso (para archivos, buffers y otros flujos de E/S que admiten [`seek`](@ref)), y [`first`](@ref) o [`last`](@ref) se pueden usar para extraer las líneas iniciales o finales, respectivamente.

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang is a GitHub organization.\n It has many members.\n");

julia> for line in eachline("my_file.txt")
           print(line)
       end
JuliaLang is a GitHub organization. It has many members.

julia> rm("my_file.txt");
```

!!! compat "Julia 1.8"
    Se requiere Julia 1.8 para usar `Iterators.reverse` o `last` con iteradores `eachline`.

