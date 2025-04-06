```
atan(y)
atan(y, x)
```

Berechne den inversen Tangens von `y` oder `y/x`, jeweils.

Für ein reales Argument ist dies der Winkel in Bogenmaß zwischen der positiven *x*-Achse und dem Punkt (1, *y*), wobei ein Wert im Intervall $[-\pi/2, \pi/2]$ zurückgegeben wird.

Für zwei Argumente ist dies der Winkel in Bogenmaß zwischen der positiven *x*-Achse und dem Punkt (*x*, *y*), wobei ein Wert im Intervall $[-\pi, \pi]$ zurückgegeben wird. Dies entspricht einer standardmäßigen [`atan2`](https://en.wikipedia.org/wiki/Atan2) Funktion. Beachte, dass konventionell `atan(0.0,x)` als $\pi$ definiert ist und `atan(-0.0,x)` als $-\pi$, wenn `x < 0`.

Siehe auch [`atand`](@ref) für Grad.

# Beispiele

```jldoctest
julia> rad2deg(atan(-1/√3))
-30.000000000000004

julia> rad2deg(atan(-1, √3))
-30.000000000000004

julia> rad2deg(atan(1, -√3))
150.0
```
