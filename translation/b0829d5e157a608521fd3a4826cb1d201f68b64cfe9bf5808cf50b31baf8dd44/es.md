```
closewrite(stream)
```

Cierra la mitad de escritura de un flujo de E/S de doble dirección. Realiza un [`flush`](@ref) primero. Notifica al otro extremo que no se escribirá más datos en el archivo subyacente. Esto no es compatible con todos los tipos de E/S.

Si se implementa, `closewrite` provoca que las llamadas subsiguientes a `read` o `eof` que bloquearían, en su lugar lancen EOF o devuelvan verdadero, respectivamente. Si el flujo ya está cerrado, esto es idempotente.

# Ejemplos

```jldoctest
julia> io = Base.BufferStream(); # esto nunca bloquea, así que podemos leer y escribir en la misma Tarea

julia> write(io, "request");

julia> # llamar a `read(io)` aquí bloquearía para siempre

julia> closewrite(io);

julia> read(io, String)
"request"
```
