```
Sys.username() -> String
```

Devuelve el nombre de usuario del usuario actual. Si no se puede determinar el nombre de usuario o está vacío, esta función lanza un error.

Para recuperar un nombre de usuario que se puede sobrescribir a través de una variable de entorno, por ejemplo, `USER`, considera usar

```julia
user = get(Sys.username, ENV, "USER")
```

!!! compat "Julia 1.11"
    Esta función requiere al menos Julia 1.11.


Consulta también [`homedir`](@ref).
