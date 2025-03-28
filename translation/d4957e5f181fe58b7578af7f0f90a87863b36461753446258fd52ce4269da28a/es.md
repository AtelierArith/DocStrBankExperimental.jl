```
circcopy!(dest, src)
```

Copia `src` a `dest`, indexando cada dimensión módulo su longitud. `src` y `dest` deben tener el mismo tamaño, pero pueden estar desplazados en sus índices; cualquier desplazamiento resulta en un envolvimiento (circular). Si los arreglos tienen índices superpuestos, entonces en el dominio de la superposición `dest` coincide con `src`.

!!! warning
    El comportamiento puede ser inesperado cuando cualquier argumento mutado comparte memoria con cualquier otro argumento.


Véase también: [`circshift`](@ref).

# Ejemplos

```julia-repl
julia> src = reshape(Vector(1:16), (4,4))
4×4 Array{Int64,2}:
 1  5   9  13
 2  6  10  14
 3  7  11  15
 4  8  12  16

julia> dest = OffsetArray{Int}(undef, (0:3,2:5))

julia> circcopy!(dest, src)
OffsetArrays.OffsetArray{Int64,2,Array{Int64,2}} with indices 0:3×2:5:
 8  12  16  4
 5   9  13  1
 6  10  14  2
 7  11  15  3

julia> dest[1:3,2:4] == src[1:3,2:4]
true
```
