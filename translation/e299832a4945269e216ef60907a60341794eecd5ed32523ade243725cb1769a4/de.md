```
cumprod!(y::AbstractVector, x::AbstractVector)
```

Kumulative Produkt eines Vektors `x`, wobei das Ergebnis in `y` gespeichert wird. Siehe auch [`cumprod`](@ref).

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.

