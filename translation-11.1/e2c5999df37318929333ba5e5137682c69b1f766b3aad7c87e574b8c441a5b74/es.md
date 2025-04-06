```
isreadable(path::String)
```

Devuelve `true` si los permisos de acceso para la `ruta` dada permiten la lectura por parte del usuario actual.

!!! note
    Este permiso puede cambiar antes de que el usuario llame a `open`, por lo que se recomienda simplemente llamar a `open` solo y manejar el error si eso falla, en lugar de llamar a `isreadable` primero.


!!! note
    Actualmente, esta función no interroga correctamente los ACL del sistema de archivos en Windows, por lo que puede devolver resultados incorrectos.


!!! compat "Julia 1.11"
    Esta función requiere al menos Julia 1.11.


Véase también [`ispath`](@ref), [`isexecutable`](@ref), [`iswritable`](@ref). ```
