```
BigFloat(x::Union{Real, AbstractString} [, rounding::RoundingMode=rounding(BigFloat)]; [precision::Integer=precision(BigFloat)])
```

Erstellen Sie eine Fließkommazahl mit beliebiger Genauigkeit aus `x`, mit der Genauigkeit `precision`. Das Argument `rounding` gibt die Richtung an, in die das Ergebnis gerundet werden soll, wenn die Umwandlung nicht genau durchgeführt werden kann. Wenn nicht angegeben, werden diese durch die aktuellen globalen Werte festgelegt.

`BigFloat(x::Real)` ist dasselbe wie `convert(BigFloat,x)`, es sei denn, `x` selbst ist bereits `BigFloat`, in diesem Fall wird ein Wert mit der Genauigkeit zurückgegeben, die auf die aktuelle globale Genauigkeit eingestellt ist; `convert` gibt immer `x` zurück.

`BigFloat(x::AbstractString)` ist identisch mit [`parse`](@ref). Dies wird zur Bequemlichkeit bereitgestellt, da Dezimalliterale beim Parsen in `Float64` umgewandelt werden, sodass `BigFloat(2.1)` möglicherweise nicht das ergibt, was Sie erwarten.

Siehe auch:

  * [`@big_str`](@ref)
  * [`rounding`](@ref) und [`setrounding`](@ref)
  * [`precision`](@ref) und [`setprecision`](@ref)

!!! compat "Julia 1.1"
    `precision` als Schlüsselwortargument erfordert mindestens Julia 1.1. In Julia 1.0 ist `precision` das zweite positionsgebundene Argument (`BigFloat(x, precision)`).


# Beispiele

```jldoctest
julia> BigFloat(2.1) # 2.1 hier ist ein Float64
2.100000000000000088817841970012523233890533447265625

julia> BigFloat("2.1") # die nächstgelegene BigFloat zu 2.1
2.099999999999999999999999999999999999999999999999999999999999999999999999999986

julia> BigFloat("2.1", RoundUp)
2.100000000000000000000000000000000000000000000000000000000000000000000000000021

julia> BigFloat("2.1", RoundUp, precision=128)
2.100000000000000000000000000000000000007
```
