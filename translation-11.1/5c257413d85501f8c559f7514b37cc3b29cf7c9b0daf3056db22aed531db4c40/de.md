```
cumprod!(B, A; dims::Integer)
```

Kumulative Produkt von `A` entlang der Dimension `dims`, wobei das Ergebnis in `B` gespeichert wird. Siehe auch [`cumprod`](@ref).

!!! warning
    Das Verhalten kann unerwartet sein, wenn ein veränderter Parameter Speicher mit einem anderen Parameter teilt.

