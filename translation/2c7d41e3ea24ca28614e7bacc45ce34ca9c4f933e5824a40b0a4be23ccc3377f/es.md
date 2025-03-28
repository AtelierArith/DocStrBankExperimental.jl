```
posición(es)
```

Obtén la posición actual de un flujo.

# Ejemplos

```jldoctest
julia> io = IOBuffer("JuliaLang es una organización de GitHub.");

julia> seek(io, 5);

julia> position(io)
5

julia> skip(io, 10);

julia> position(io)
15

julia> seekend(io);

julia> position(io)
35
```
