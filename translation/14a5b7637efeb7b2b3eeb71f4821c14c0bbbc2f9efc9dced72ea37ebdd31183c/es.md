```
touch(path::AbstractString)
touch(fd::File)
```

Actualiza la marca de tiempo de la última modificación de un archivo a la hora actual.

Si el archivo no existe, se crea un nuevo archivo.

Devuelve `path`.

# Ejemplos

```julia-repl
julia> write("my_little_file", 2);

julia> mtime("my_little_file")
1.5273815391135583e9

julia> touch("my_little_file");

julia> mtime("my_little_file")
1.527381559163435e9
```

Podemos ver que [`mtime`](@ref) ha sido modificado por `touch`.
