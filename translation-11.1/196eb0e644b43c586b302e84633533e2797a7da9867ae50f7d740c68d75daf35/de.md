```
isbitstype(T)
```

Gibt `true` zurück, wenn der Typ `T` ein "einfacher Datentyp" ist, was bedeutet, dass er unveränderlich ist und keine Verweise auf andere Werte enthält, sondern nur `primitive` Typen und andere `isbitstype` Typen. Typische Beispiele sind numerische Typen wie [`UInt8`](@ref), [`Float64`](@ref) und [`Complex{Float64}`](@ref). Diese Kategorie von Typen ist bedeutend, da sie als Typparameter gültig sind, möglicherweise den Status [`isdefined`](@ref) / [`isassigned`](@ref) nicht verfolgen und ein definiertes Layout haben, das mit C kompatibel ist. Wenn `T` kein Typ ist, wird `false` zurückgegeben.

Siehe auch [`isbits`](@ref), [`isprimitivetype`](@ref), [`ismutable`](@ref).

# Beispiele

```jldoctest
julia> isbitstype(Complex{Float64})
true

julia> isbitstype(Complex)
false
```
