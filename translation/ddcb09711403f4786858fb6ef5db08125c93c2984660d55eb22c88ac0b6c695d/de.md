```
subtypen(T::DataType)
```

Gibt eine Liste der unmittelbaren Subtypen des DataType `T` zurück. Beachten Sie, dass alle derzeit geladenen Subtypen enthalten sind, einschließlich derjenigen, die im aktuellen Modul nicht sichtbar sind.

Siehe auch [`supertype`](@ref), [`supertypes`](@ref), [`methodswith`](@ref).

# Beispiele

```jldoctest
julia> subtypen(Integer)
3-element Vector{Any}:
 Bool
 Signed
 Unsigned
```
