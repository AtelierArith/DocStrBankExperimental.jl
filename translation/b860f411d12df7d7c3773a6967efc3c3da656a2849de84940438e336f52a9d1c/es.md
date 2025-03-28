```
readdlm(source; options...)
```

Se asume que las columnas están separadas por uno o más espacios en blanco. El delimitador de fin de línea se toma como `\n`. Si todos los datos son numéricos, el resultado será un arreglo numérico. Si algunos elementos no se pueden analizar como números, se devuelve un arreglo heterogéneo de números y cadenas.

# Ejemplos

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = ["a"; "b"; "c"; "d"];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end;

julia> readdlm("delim_file.txt")
4×2 Matrix{Any}:
 1  "a"
 2  "b"
 3  "c"
 4  "d"

julia> rm("delim_file.txt")
```
