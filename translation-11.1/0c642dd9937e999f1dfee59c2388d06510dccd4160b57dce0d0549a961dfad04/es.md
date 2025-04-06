```
isopen(object) -> Bool
```

Determina si un objeto - como un flujo o un temporizador - no está cerrado aún. Una vez que un objeto está cerrado, nunca producirá un nuevo evento. Sin embargo, dado que un flujo cerrado puede aún tener datos para leer en su búfer, utiliza [`eof`](@ref) para verificar la capacidad de leer datos. Usa el paquete `FileWatching` para ser notificado cuando un flujo pueda ser escribible o legible.

# Ejemplos

```jldoctest
julia> io = open("my_file.txt", "w+");

julia> isopen(io)
true

julia> close(io)

julia> isopen(io)
false
```
