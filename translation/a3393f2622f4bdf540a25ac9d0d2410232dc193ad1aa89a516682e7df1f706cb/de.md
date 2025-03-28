```
Sys.isdragonfly([os])
```

Prädikat zum Testen, ob das Betriebssystem eine Abspaltung von DragonFly BSD ist. Siehe Dokumentation in [Handling Operating System Variation](@ref).

!!! Hinweis     Nicht zu verwechseln mit `Sys.isbsd()`, das `true` auf DragonFly, aber auch auf anderen BSD-basierten Systemen ist. `Sys.isdragonfly()` bezieht sich nur auf DragonFly.

!!! kompatibel "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.

