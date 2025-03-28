```
sizeof(T::DataType)
sizeof(obj)
```

Tamaño, en bytes, de la representación binaria canónica del `DataType` dado `T`, si existe. O el tamaño, en bytes, del objeto `obj` si no es un `DataType`.

Véase también [`Base.summarysize`](@ref).

# Ejemplos

```jldoctest
julia> sizeof(Float32)
4

julia> sizeof(ComplexF64)
16

julia> sizeof(1.0)
8

julia> sizeof(collect(1.0:10.0))
80

julia> struct StructWithPadding
           x::Int64
           flag::Bool
       end

julia> sizeof(StructWithPadding) # no es la suma de `sizeof` de los campos debido al relleno
16

julia> sizeof(Int64) + sizeof(Bool) # diferente de arriba
9
```

Si el `DataType` `T` no tiene un tamaño específico, se lanza un error.

```jldoctest
julia> sizeof(AbstractArray)
ERROR: El tipo abstracto AbstractArray no tiene un tamaño definido.
Stacktrace:
[...]
```
