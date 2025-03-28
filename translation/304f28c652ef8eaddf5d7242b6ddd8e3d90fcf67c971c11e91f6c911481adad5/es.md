```
@sprintf("%Fmt", args...)
```

Devuelve la salida formateada de [`@printf`](@ref) como cadena.

# Ejemplos

```jldoctest
julia> @sprintf "esto es un %s %15.1f" "prueba" 34.567
"esto es un prueba            34.6"
```
