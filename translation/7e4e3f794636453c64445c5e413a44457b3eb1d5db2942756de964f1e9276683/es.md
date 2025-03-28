```
IOBuffer([data::AbstractVector{UInt8}]; keywords...) -> IOBuffer
```

Crea un flujo de I/O en memoria, que puede operar opcionalmente sobre un arreglo preexistente.

Puede tomar argumentos de palabra clave opcionales:

  * `read`, `write`, `append`: restringe las operaciones al búfer; consulta `open` para más detalles.
  * `truncate`: trunca el tamaño del búfer a cero.
  * `maxsize`: especifica un tamaño más allá del cual el búfer no puede crecer.
  * `sizehint`: sugiere una capacidad del búfer (`data` debe implementar `sizehint!(data, size)`).

Cuando `data` no se proporciona, el búfer será tanto legible como escribible por defecto.

# Ejemplos

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang is a GitHub organization.", " It has many members.")
56

julia> String(take!(io))
"JuliaLang is a GitHub organization. It has many members."

julia> io = IOBuffer(b"JuliaLang is a GitHub organization.")
IOBuffer(data=UInt8[...], readable=true, writable=false, seekable=true, append=false, size=35, maxsize=Inf, ptr=1, mark=-1)

julia> read(io, String)
"JuliaLang is a GitHub organization."

julia> write(io, "This isn't writable.")
ERROR: ArgumentError: ensureroom failed, IOBuffer is not writeable

julia> io = IOBuffer(UInt8[], read=true, write=true, maxsize=34)
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=34, ptr=1, mark=-1)

julia> write(io, "JuliaLang is a GitHub organization.")
34

julia> String(take!(io))
"JuliaLang is a GitHub organization"

julia> length(read(IOBuffer(b"data", read=true, truncate=false)))
4

julia> length(read(IOBuffer(b"data", read=true, truncate=true)))
0
```
