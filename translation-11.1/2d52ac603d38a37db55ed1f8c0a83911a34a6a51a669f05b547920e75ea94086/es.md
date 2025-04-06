```
eof(stream) -> Bool
```

Prueba si un flujo de E/S está al final del archivo. Si el flujo aún no se ha agotado, esta función bloqueará para esperar más datos si es necesario, y luego devolverá `false`. Por lo tanto, siempre es seguro leer un byte después de ver que `eof` devuelve `false`. `eof` devolverá `false` mientras haya datos en búfer disponibles, incluso si el extremo remoto de una conexión está cerrado.

# Ejemplos

```jldoctest
julia> b = IOBuffer("my buffer");

julia> eof(b)
false

julia> seekend(b);

julia> eof(b)
true
```
