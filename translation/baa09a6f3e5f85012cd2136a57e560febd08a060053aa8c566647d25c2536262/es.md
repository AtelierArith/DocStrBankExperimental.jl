```
reinterpret(::Type{Out}, x::In)
```

Cambia la interpretación de tipo de los datos binarios en el valor isbits `x` al tipo isbits `Out`. El tamaño (ignorando el relleno) de `Out` tiene que ser el mismo que el del tipo de `x`. Por ejemplo, `reinterpret(Float32, UInt32(7))` interpreta los 4 bytes correspondientes a `UInt32(7)` como un [`Float32`](@ref). Ten en cuenta que `reinterpret(In, reinterpret(Out, x)) === x`

```jldoctest
julia> reinterpret(Float32, UInt32(7))
1.0f-44

julia> reinterpret(NTuple{2, UInt8}, 0x1234)
(0x34, 0x12)

julia> reinterpret(UInt16, (0x34, 0x12))
0x1234

julia> reinterpret(Tuple{UInt16, UInt8}, (0x01, 0x0203))
(0x0301, 0x02)
```

!!! note
    El tratamiento del relleno difiere de reinterpret(::DataType, ::AbstractArray).


!!! warning
    Ten cuidado si algunas combinaciones de bits en `Out` no se consideran válidas y de otro modo serían prevenidas por los constructores y métodos del tipo. Puede resultar un comportamiento inesperado sin una validación adicional.

