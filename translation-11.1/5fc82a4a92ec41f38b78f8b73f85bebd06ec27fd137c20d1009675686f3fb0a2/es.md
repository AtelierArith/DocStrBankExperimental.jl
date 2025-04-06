```
eltype(type)
```

Determina el tipo de los elementos generados al iterar una colección del `type` dado. Para los tipos de diccionario, esto será un `Pair{KeyType,ValType}`. La definición `eltype(x) = eltype(typeof(x))` se proporciona por conveniencia para que se puedan pasar instancias en lugar de tipos. Sin embargo, la forma que acepta un argumento de tipo debe definirse para nuevos tipos.

Véase también: [`keytype`](@ref), [`typeof`](@ref).

# Ejemplos

```jldoctest
julia> eltype(fill(1f0, (2,2)))
Float32

julia> eltype(fill(0x1, (2,2)))
UInt8
```
