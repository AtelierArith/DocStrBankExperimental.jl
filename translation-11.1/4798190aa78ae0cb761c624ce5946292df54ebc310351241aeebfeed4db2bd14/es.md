```
ENV
```

Referencia al singleton `EnvDict`, que proporciona una interfaz de diccionario a las variables de entorno del sistema.

(En Windows, las variables de entorno del sistema no son sensibles a mayúsculas y minúsculas, y `ENV` convierte correspondientemente todas las claves a mayúsculas para su visualización, iteración y copia. El código portátil no debe depender de la capacidad de distinguir variables por caso, y debe tener cuidado de que establecer una variable aparentemente en minúsculas puede resultar en una clave `ENV` en mayúsculas.)

!!! advertencia
    Mutar el entorno no es seguro para hilos.


# Ejemplos

```julia-repl
julia> ENV
Base.EnvDict con "50" entradas:
  "SECURITYSESSIONID"            => "123"
  "USER"                         => "nombredeusuario"
  "MallocNanoZone"               => "0"
  ⋮                              => ⋮

julia> ENV["JULIA_EDITOR"] = "vim"
"vim"

julia> ENV["JULIA_EDITOR"]
"vim"
```

Ver también: [`withenv`](@ref), [`addenv`](@ref).
