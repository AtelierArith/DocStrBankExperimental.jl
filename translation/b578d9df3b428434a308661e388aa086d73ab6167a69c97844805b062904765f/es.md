```
promote(xs...)
```

Convierte todos los argumentos a un tipo común y los devuelve todos (como una tupla). Si no se pueden convertir argumentos, se genera un error.

Véase también: [`promote_type`](@ref), [`promote_rule`](@ref).

# Ejemplos

```jldoctest
julia> promote(Int8(1), Float16(4.5), Float32(4.1))
(1.0f0, 4.5f0, 4.1f0)

julia> promote_type(Int8, Float16, Float32)
Float32

julia> reduce(Base.promote_typejoin, (Int8, Float16, Float32))
Real

julia> promote(1, "x")
ERROR: la promoción de tipos Int64 y String no pudo cambiar ningún argumento
[...]

julia> promote_type(Int, String)
Any
```
