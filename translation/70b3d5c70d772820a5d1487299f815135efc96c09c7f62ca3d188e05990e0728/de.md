```
Sys.isnetbsd([os])
```

Prädikat zum Testen, ob das Betriebssystem ein Derivat von NetBSD ist. Siehe Dokumentation in [Handling Operating System Variation](@ref).

!!! Hinweis     Nicht zu verwechseln mit `Sys.isbsd()`, das auf NetBSD, aber auch auf anderen BSD-basierten Systemen `true` ist. `Sys.isnetbsd()` bezieht sich nur auf NetBSD.

!!! Kompatibilität "Julia 1.1"     Diese Funktion erfordert mindestens Julia 1.1.
