```
mod2pi(x)
```

Modulus nach Division durch `2π`, Rückgabe im Bereich $[0,2π)$.

Diese Funktion berechnet eine Fließkommadarstellung des Modulus nach Division durch numerisch exaktes `2π` und ist daher nicht genau dasselbe wie `mod(x,2π)`, das den Modulus von `x` relativ zur Division durch die Fließkommazahl `2π` berechnen würde.

!!! Hinweis     Abhängig vom Format des Eingabewerts kann der nächstgelegene darstellbare Wert zu 2π kleiner als 2π sein. Zum Beispiel wird der Ausdruck `mod2pi(2π)` nicht `0` zurückgeben, da der Zwischenwert von `2*π` ein `Float64` ist und `2*Float64(π) < 2*big(π)`. Siehe [`rem2pi`](@ref) für eine verfeinerte Kontrolle dieses Verhaltens.

# Beispiele

```jldoctest
julia> mod2pi(9*pi/4)
0.7853981633974481
```
