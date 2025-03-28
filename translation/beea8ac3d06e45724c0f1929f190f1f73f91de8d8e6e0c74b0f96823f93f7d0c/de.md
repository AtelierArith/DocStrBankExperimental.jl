```
fma(x, y, z)
```

Berechnet `x*y+z` ohne das Zwischenergebnis `x*y` zu runden. Auf einigen Systemen ist dies erheblich teurer als `x*y+z`. `fma` wird verwendet, um die Genauigkeit in bestimmten Algorithmen zu verbessern. Siehe [`muladd`](@ref).
