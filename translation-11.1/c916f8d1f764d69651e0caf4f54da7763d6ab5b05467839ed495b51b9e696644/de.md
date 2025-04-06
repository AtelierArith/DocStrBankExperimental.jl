```
extrema(f, itr; [init]) -> (mn, mx)
```

Berechne sowohl das Minimum `mn` als auch das Maximum `mx` von `f`, angewendet auf jedes Element in `itr`, und gib sie als 2-Tupel zurück. Es wird nur ein Durchlauf über `itr` gemacht.

Der zurückgegebene Wert für ein leeres `itr` kann durch `init` spezifiziert werden. Es muss ein 2-Tupel sein, dessen erstes und zweites Element neutrale Elemente für `min` und `max` sind (d.h. die größer/kleiner als oder gleich jedem anderen Element sind). Es wird für nicht-leere Sammlungen verwendet. Hinweis: Es impliziert, dass für ein leeres `itr` der zurückgegebene Wert `(mn, mx)` die Bedingung `mn ≥ mx` erfüllt, obwohl für ein nicht-leeres `itr` die Bedingung `mn ≤ mx` erfüllt ist. Dies ist ein "paradoxer", aber dennoch erwarteter Effekt.

!!! compat "Julia 1.2"
    Diese Methode erfordert Julia 1.2 oder höher.


!!! compat "Julia 1.8"
    Das Schlüsselwort-Argument `init` erfordert Julia 1.8 oder höher.


# Beispiele

```jldoctest
julia> extrema(sin, 0:π)
(0.0, 0.9092974268256817)

julia> extrema(sin, Real[]; init = (1.0, -1.0))  # gut, da -1 ≤ sin(::Real) ≤ 1
(1.0, -1.0)
```
