```
FILE(::Ptr)
FILE(::IO)
```

Un `FILE*` de libc, que representa un archivo abierto.

Se puede pasar como un argumento `Ptr{FILE}` a [`ccall`](@ref) y también soporta [`seek`](@ref), [`position`](@ref) y [`close`](@ref).

Un `FILE` se puede construir a partir de un objeto `IO` ordinario, siempre que sea un archivo abierto. Debe cerrarse después.

# Ejemplos

```jldoctest
julia> using Base.Libc

julia> mktemp() do _, io
           # escribir en el archivo temporal usando `puts(char*, FILE*)` de libc
           file = FILE(io)
           ccall(:fputs, Cint, (Cstring, Ptr{FILE}), "hello world", file)
           close(file)
           # leer el archivo nuevamente
           seek(io, 0)
           read(io, String)
       end
"hello world"
```
