```
walkdir(dir; topdown=true, follow_symlinks=false, onerror=throw)
```

Devuelve un iterador que recorre el árbol de directorios de un directorio. El iterador devuelve una tupla que contiene `(rootpath, dirs, files)`. El árbol de directorios se puede recorrer de arriba hacia abajo o de abajo hacia arriba. Si `walkdir` o `stat` encuentra un `IOError`, volverá a lanzar el error por defecto. Se puede proporcionar una función de manejo de errores personalizada a través del argumento clave `onerror`. `onerror` se llama con un `IOError` como argumento.

Véase también: [`readdir`](@ref).

# Ejemplos

```julia
for (root, dirs, files) in walkdir(".")
    println("Directorios en $root")
    for dir in dirs
        println(joinpath(root, dir)) # ruta a directorios
    end
    println("Archivos en $root")
    for file in files
        println(joinpath(root, file)) # ruta a archivos
    end
end
```

```julia-repl
julia> mkpath("my/test/dir");

julia> itr = walkdir("my");

julia> (root, dirs, files) = first(itr)
("my", ["test"], String[])

julia> (root, dirs, files) = first(itr)
("my/test", ["dir"], String[])

julia> (root, dirs, files) = first(itr)
("my/test/dir", String[], String[])
```
