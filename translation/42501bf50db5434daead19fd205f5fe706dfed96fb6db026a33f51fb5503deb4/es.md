```
isimmutable(v) -> Bool
```

!!! warning
    Considera usar `!ismutable(v)` en su lugar, ya que `isimmutable(v)` será reemplazado por `!ismutable(v)` en una futura versión. (Desde Julia 1.5)


Devuelve `true` si y solo si el valor `v` es inmutable. Consulta [Tipos Compuestos Mutables](@ref) para una discusión sobre la inmutabilidad. Ten en cuenta que esta función trabaja con valores, por lo que si le das un tipo, te dirá que un valor de `DataType` es mutable.

# Ejemplos

```jldoctest
julia> isimmutable(1)
true

julia> isimmutable([1,2])
false
```
