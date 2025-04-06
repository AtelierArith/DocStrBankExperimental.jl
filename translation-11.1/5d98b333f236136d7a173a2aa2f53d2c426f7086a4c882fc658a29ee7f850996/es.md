```
Experimental.show_error_hints(io, ex, args...)
```

Invoca todos los controladores de [`Experimental.register_error_hint`](@ref) para el tipo de excepción particular `typeof(ex)`. `args` debe contener cualquier otro argumento esperado por el controlador para ese tipo.

!!! compat "Julia 1.5"
    Las sugerencias de error personalizadas están disponibles a partir de Julia 1.5.


!!! warning
    Esta interfaz es experimental y está sujeta a cambios o eliminación sin previo aviso.

