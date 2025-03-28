```
isexecutable(path::String)
```

Devuelve `true` si el `path` dado tiene permisos de ejecución.

!!! note
    Este permiso puede cambiar antes de que el usuario ejecute `path`, por lo que se recomienda ejecutar el archivo y manejar el error si eso falla, en lugar de llamar a `isexecutable` primero.


!!! note
    Antes de Julia 1.6, esto no interrogaba correctamente los ACL del sistema de archivos en Windows, por lo que devolvería `true` para cualquier archivo. A partir de Julia 1.6, determina correctamente si el archivo está marcado como ejecutable o no.


Véase también [`ispath`](@ref), [`isreadable`](@ref), [`iswritable`](@ref).
