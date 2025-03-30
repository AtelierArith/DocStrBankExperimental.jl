```
NaN, NaN64
```

[`Float64`](@ref) türünde bir not-a-number değeri.

Ayrıca bakınız: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# Örnekler

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! not
    `NaN` kontrolü için her zaman [`isnan`](@ref) veya [`isequal`](@ref) kullanın. `x === NaN` kullanmak beklenmedik sonuçlar verebilir:

    ```julia-repl
    julia> reinterpret(UInt32, NaN32)
    0x7fc00000

    julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
    NaN32

    julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
    (false, true, true)
    ```

