```
skipchars(predicate, io::IO; linecomment=nothing)
```

Avanza el flujo `io` de tal manera que el siguiente carácter que se lea será el primero restante para el cual `predicate` devuelve `false`. Si se especifica el argumento clave `linecomment`, se ignoran todos los caracteres desde ese carácter hasta el inicio de la siguiente línea.

# Ejemplos

```jldoctest
julia> buf = IOBuffer("    text")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=1, mark=-1)

julia> skipchars(isspace, buf)
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=8, maxsize=Inf, ptr=5, mark=-1)

julia> String(readavailable(buf))
"text"
```
