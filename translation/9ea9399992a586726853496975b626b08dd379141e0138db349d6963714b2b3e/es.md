```
writedlm(f, A, delim='\t'; opts)
```

Escribe `A` (un vector, matriz o una colección iterable de filas iterables) como texto en `f` (ya sea una cadena de nombre de archivo o un flujo `IO`) utilizando el delimitador dado `delim` (que por defecto es tabulador, pero puede ser cualquier objeto imprimible de Julia, típicamente un `Char` o `AbstractString`).

Por ejemplo, dos vectores `x` e `y` de la misma longitud se pueden escribir como dos columnas de texto delimitado por tabuladores en `f` ya sea con `writedlm(f, [x y])` o con `writedlm(f, zip(x, y))`.

# Ejemplos

```jldoctest
julia> using DelimitedFiles

julia> x = [1; 2; 3; 4];

julia> y = [5; 6; 7; 8];

julia> open("delim_file.txt", "w") do io
           writedlm(io, [x y])
       end

julia> readdlm("delim_file.txt", '\t', Int, '\n')
4×2 Matrix{Int64}:
 1  5
 2  6
 3  7
 4  8

julia> rm("delim_file.txt")
```
