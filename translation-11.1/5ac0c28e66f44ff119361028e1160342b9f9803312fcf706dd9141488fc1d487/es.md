```
countlines(io::IO; eol::AbstractChar = '\n')
countlines(filename::AbstractString; eol::AbstractChar = '\n')
```

Lee `io` hasta el final del flujo/archivo y cuenta el número de líneas. Para especificar un archivo, pasa el nombre del archivo como el primer argumento. Se admiten marcadores EOL distintos de `'\n'` pasándolos como el segundo argumento. La última línea no vacía de `io` se cuenta incluso si no termina con el EOL, coincidiendo con la longitud devuelta por [`eachline`](@ref) y [`readlines`](@ref).

Para contar líneas de un `String`, se puede usar `countlines(IOBuffer(str))`.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub.\n");

julia> countlines(io)
1

julia> io = IOBuffer("JuliaLang es una organización de GitHub.");

julia> countlines(io)
1

julia> eof(io) # contar líneas mueve el puntero del archivo
true

julia> io = IOBuffer("JuliaLang es una organización de GitHub.");

julia> countlines(io, eol = '.')
1
```

```jldoctest
julia> write("mi_archivo.txt", "JuliaLang es una organización de GitHub.\n")
36

julia> countlines("mi_archivo.txt")
1

julia> countlines("mi_archivo.txt", eol = 'n')
4

julia> rm("mi_archivo.txt")

```
