```
NaN, NaN64
```

Un valor no numérico de tipo [`Float64`](@ref).

Véase también: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# Ejemplos

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! nota
    Siempre usa [`isnan`](@ref) o [`isequal`](@ref) para verificar `NaN`. Usar `x === NaN` puede dar resultados inesperados:

    ```julia-repl
    julia> reinterpret(UInt32, NaN32)
    0x7fc00000

    julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
    NaN32

    julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
    (false, true, true)
    ```

