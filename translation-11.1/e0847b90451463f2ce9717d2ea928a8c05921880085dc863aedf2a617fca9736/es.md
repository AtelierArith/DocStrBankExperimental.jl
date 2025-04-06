```
ismutable(v) -> Bool
```

Devuelve `true` si y solo si el valor `v` es mutable. Consulta [Tipos Compuestos Mutables](@ref) para una discusión sobre la inmutabilidad. Ten en cuenta que esta función trabaja con valores, por lo que si le das un `DataType`, te dirá que un valor del tipo es mutable.

!!! nota
    Por razones técnicas, `ismutable` devuelve `true` para valores de ciertos tipos especiales (por ejemplo `String` y `Symbol`) aunque no se puedan mutar de una manera permisible.


Consulta también [`isbits`](@ref), [`isstructtype`](@ref).

# Ejemplos

```jldoctest
julia> ismutable(1)
false

julia> ismutable([1,2])
true
```

!!! compat "Julia 1.5"
    Esta función requiere al menos Julia 1.5.

