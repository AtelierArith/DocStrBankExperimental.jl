```
readchomp(x)
```

Lee la totalidad de `x` como una cadena y elimina un solo salto de línea final si existe. Equivalente a `chomp(read(x, String))`.

# Ejemplos

```jldoctest
julia> write("my_file.txt", "JuliaLang es una organización de GitHub.\nTiene muchos miembros.\n");

julia> readchomp("my_file.txt")
"JuliaLang es una organización de GitHub.\nTiene muchos miembros."

julia> rm("my_file.txt");
```
