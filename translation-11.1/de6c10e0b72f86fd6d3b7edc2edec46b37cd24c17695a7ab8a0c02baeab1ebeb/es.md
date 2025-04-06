```
write(io::IO, x)
```

Escribe la representación binaria canónica de un valor en el flujo de E/S o archivo dado. Devuelve el número de bytes escritos en el flujo. Consulta también [`print`](@ref) para escribir una representación de texto (con una codificación que puede depender de `io`).

El orden de bytes del valor escrito depende del orden de bytes del sistema anfitrión. Convierte a/desde un orden de bytes fijo al escribir/leer (por ejemplo, usando [`htol`](@ref) y [`ltoh`](@ref)) para obtener resultados que sean consistentes en todas las plataformas.

Puedes escribir múltiples valores con la misma llamada a `write`. Es decir, lo siguiente es equivalente:

```
write(io, x, y...)
write(io, x) + write(io, y...)
```

# Ejemplos

Serialización consistente:

```jldoctest
julia> fname = tempname(); # nombre de archivo temporal aleatorio

julia> open(fname,"w") do f
           # Asegúrate de que escribimos un entero de 64 bits en orden de bytes little-endian
           write(f,htol(Int64(42)))
       end
8

julia> open(fname,"r") do f
           # Convierte de nuevo al orden de bytes del anfitrión y al tipo de entero del anfitrión
           Int(ltoh(read(f,Int64)))
       end
42
```

Fusionando llamadas a write:

```jldoctest
julia> io = IOBuffer();

julia> write(io, "JuliaLang es una organización de GitHub.", " Tiene muchos miembros.")
56

julia> String(take!(io))
"JuliaLang es una organización de GitHub. Tiene muchos miembros."

julia> write(io, "A veces esos miembros") + write(io, " escriben documentación.")
44

julia> String(take!(io))
"A veces esos miembros escriben documentación."
```

Los tipos de datos simples definidos por el usuario sin métodos `write` pueden escribirse cuando están envueltos en un `Ref`:

```jldoctest
julia> struct MyStruct; x::Float64; end

julia> io = IOBuffer()
IOBuffer(data=UInt8[...], readable=true, writable=true, seekable=true, append=false, size=0, maxsize=Inf, ptr=1, mark=-1)

julia> write(io, Ref(MyStruct(42.0)))
8

julia> seekstart(io); read!(io, Ref(MyStruct(NaN)))
Base.RefValue{MyStruct}(MyStruct(42.0))
```
