```
eps(x::AbstractFloat)
```

Gibt die *Einheit im letzten Platz* (ulp) von `x` zurück. Dies ist der Abstand zwischen aufeinanderfolgenden darstellbaren Gleitkommawerten bei `x`. In den meisten Fällen, wenn der Abstand auf beiden Seiten von `x` unterschiedlich ist, wird der größere der beiden genommen, das heißt

```
eps(x) == max(x-prevfloat(x), nextfloat(x)-x)
```

Die Ausnahmen von dieser Regel sind die kleinsten und größten endlichen Werte (z. B. `nextfloat(-Inf)` und `prevfloat(Inf)` für [`Float64`](@ref)), die auf den kleineren der Werte gerundet werden.

Die Begründung für dieses Verhalten ist, dass `eps` den Gleitkomma-Rundungsfehler begrenzt. Im Standard-Rundungsmodus `RoundNearest`, wenn $y$ eine reelle Zahl ist und $x$ die nächstgelegene Gleitkommazahl zu $y$ ist, dann gilt

$$
|y-x| \leq \operatorname{eps}(x)/2.
$$

Siehe auch: [`nextfloat`](@ref), [`issubnormal`](@ref), [`floatmax`](@ref).

# Beispiele

```jldoctest
julia> eps(1.0)
2.220446049250313e-16

julia> eps(prevfloat(2.0))
2.220446049250313e-16

julia> eps(2.0)
4.440892098500626e-16

julia> x = prevfloat(Inf)      # größter endlicher Float64
1.7976931348623157e308

julia> x + eps(x)/2            # rundet auf
Inf

julia> x + prevfloat(eps(x)/2) # rundet ab
1.7976931348623157e308
```
