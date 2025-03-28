```
NaN, NaN64
```

Ein nicht-ein-Zahlen-Wert vom Typ [`Float64`](@ref).

Siehe auch: [`isnan`](@ref), [`missing`](@ref), [`NaN32`](@ref), [`Inf`](@ref).

# Beispiele

```jldoctest
julia> 0/0
NaN

julia> Inf - Inf
NaN

julia> NaN == NaN, isequal(NaN, NaN), isnan(NaN)
(false, true, true)
```

!!! Hinweis     Verwenden Sie immer [`isnan`](@ref) oder [`isequal`](@ref) zur Überprüfung auf `NaN`. Die Verwendung von `x === NaN` kann unerwartete Ergebnisse liefern:

````
```julia-repl
julia> reinterpret(UInt32, NaN32)
0x7fc00000

julia> NaN32p1 = reinterpret(Float32, 0x7fc00001)
NaN32

julia> NaN32p1 === NaN32, isequal(NaN32p1, NaN32), isnan(NaN32p1)
(false, true, true)
```
````
