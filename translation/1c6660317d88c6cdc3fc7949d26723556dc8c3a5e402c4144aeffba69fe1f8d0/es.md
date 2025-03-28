```
mktempdir(parent=tempdir(); prefix="jl_", cleanup=true) -> path
```

Crea un directorio temporal en el directorio `parent` con un nombre construido a partir del `prefix` dado y un sufijo aleatorio, y devuelve su ruta. Además, en algunas plataformas, cualquier carácter `'X'` final en `prefix` puede ser reemplazado por caracteres aleatorios. Si `parent` no existe, se lanzará un error. La opción `cleanup` controla si el directorio temporal se elimina automáticamente cuando el proceso finaliza.

!!! compat "Julia 1.2"
    El argumento de palabra clave `prefix` se agregó en Julia 1.2.


!!! compat "Julia 1.3"
    El argumento de palabra clave `cleanup` se agregó en Julia 1.3. Relacionado con esto, a partir de 1.3, Julia eliminará las rutas temporales creadas por `mktempdir` cuando el proceso de Julia finalice, a menos que `cleanup` se establezca explícitamente en `false`.


Ver también: [`mktemp`](@ref), [`mkdir`](@ref).
