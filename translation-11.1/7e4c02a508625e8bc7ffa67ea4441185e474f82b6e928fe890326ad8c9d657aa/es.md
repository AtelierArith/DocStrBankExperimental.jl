```
bytesavailable(io)
```

Devuelve el número de bytes disponibles para leer antes de que una lectura de este flujo o búfer bloquee.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub");

julia> bytesavailable(io)
34
```
