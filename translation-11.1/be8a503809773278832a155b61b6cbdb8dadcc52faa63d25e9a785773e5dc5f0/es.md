```
promote_type(type1, type2, ...)
```

La promoción se refiere a convertir valores de tipos mixtos a un único tipo común. `promote_type` representa el comportamiento de promoción predeterminado en Julia cuando los operadores (generalmente matemáticos) reciben argumentos de tipos diferentes. `promote_type` generalmente intenta devolver un tipo que al menos pueda aproximar la mayoría de los valores de cualquiera de los tipos de entrada sin ampliar excesivamente. Se tolera cierta pérdida; por ejemplo, `promote_type(Int64, Float64)` devuelve [`Float64`](@ref) aunque estrictamente, no todos los valores de [`Int64`](@ref) pueden ser representados exactamente como valores de `Float64`.

Véase también: [`promote`](@ref), [`promote_typejoin`](@ref), [`promote_rule`](@ref).

# Ejemplos

```jldoctest
julia> promote_type(Int64, Float64)
Float64

julia> promote_type(Int32, Int64)
Int64

julia> promote_type(Float32, BigInt)
BigFloat

julia> promote_type(Int16, Float16)
Float16

julia> promote_type(Int64, Float16)
Float16

julia> promote_type(Int8, UInt16)
UInt16
```

!!! warning "No sobrecargues esto directamente"
    Para sobrecargar la promoción para tus propios tipos, debes sobrecargar [`promote_rule`](@ref). `promote_type` llama a `promote_rule` internamente para determinar el tipo. Sobrecargar `promote_type` directamente puede causar errores de ambigüedad.

