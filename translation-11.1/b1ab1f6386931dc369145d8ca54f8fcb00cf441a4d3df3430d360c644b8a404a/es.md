```
try/catch
```

Una declaración `try`/`catch` permite interceptar errores (excepciones) lanzados por [`throw`](@ref) para que la ejecución del programa pueda continuar. Por ejemplo, el siguiente código intenta escribir un archivo, pero advierte al usuario y procede en lugar de terminar la ejecución si el archivo no se puede escribir:

```julia
try
    open("/danger", "w") do f
        println(f, "Hello")
    end
catch
    @warn "No se pudo escribir el archivo."
end
```

o, cuando el archivo no se puede leer en una variable:

```julia
lines = try
    open("/danger", "r") do f
        readlines(f)
    end
catch
    @warn "Archivo no encontrado."
end
```

La sintaxis `catch e` (donde `e` es cualquier variable) asigna el objeto de excepción lanzado a la variable dada dentro del bloque `catch`.

El poder de la construcción `try`/`catch` radica en la capacidad de deshacer una computación profundamente anidada inmediatamente a un nivel mucho más alto en la pila de funciones llamadas.
