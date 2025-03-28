```
Bool <: Integer
```

Boolescher Typ, der die Werte `true` und `false` enthält.

`Bool` ist eine Art von Zahl: `false` ist numerisch gleich `0` und `true` ist numerisch gleich `1`. Darüber hinaus wirkt `false` als multiplikativer "starker Null" gegen [`NaN`](@ref) und [`Inf`](@ref):

```jldoctest
julia> [true, false] == [1, 0]
true

julia> 42.0 + true
43.0

julia> 0 .* (NaN, Inf, -Inf)
(NaN, NaN, NaN)

julia> false .* (NaN, Inf, -Inf)
(0.0, 0.0, -0.0)
```

Verzweigungen über [`if`](@ref) und andere Bedingungen akzeptieren nur `Bool`. Es gibt keine "truthy" Werte in Julia.

Vergleiche geben typischerweise `Bool` zurück, und broadcastete Vergleiche können [`BitArray`](@ref) anstelle eines `Array{Bool}` zurückgeben.

```jldoctest
julia> [1 2 3 4 5] .< pi
1×5 BitMatrix:
 1  1  1  0  0

julia> map(>(pi), [1 2 3 4 5])
1×5 Matrix{Bool}:
 0  0  0  1  1
```

Siehe auch [`trues`](@ref), [`falses`](@ref), [`ifelse`](@ref).
