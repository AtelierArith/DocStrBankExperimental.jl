```
setrounding(f::Function, T, mode)
```

Ändert den Rundungsmodus des Fließkommatyps `T` für die Dauer von `f`. Es ist logisch äquivalent zu:

```
old = rounding(T)
setrounding(T, mode)
f()
setrounding(T, old)
```

Siehe [`RoundingMode`](@ref) für verfügbare Rundungsmodi.
