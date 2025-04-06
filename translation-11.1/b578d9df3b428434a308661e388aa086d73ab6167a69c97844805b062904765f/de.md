```
promote(xs...)
```

Konvertiere alle Argumente in einen gemeinsamen Typ und gebe sie alle (als Tuple) zurück. Wenn keine Argumente konvertiert werden können, wird ein Fehler ausgelöst.

Siehe auch: [`promote_type`](@ref), [`promote_rule`](@ref).

# Beispiele

```jldoctest
julia> promote(Int8(1), Float16(4.5), Float32(4.1))
(1.0f0, 4.5f0, 4.1f0)

julia> promote_type(Int8, Float16, Float32)
Float32

julia> reduce(Base.promote_typejoin, (Int8, Float16, Float32))
Real

julia> promote(1, "x")
ERROR: promotion of types Int64 and String failed to change any arguments
[...]

julia> promote_type(Int, String)
Any
```
