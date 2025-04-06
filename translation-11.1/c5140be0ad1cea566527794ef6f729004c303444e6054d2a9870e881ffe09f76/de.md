```
Sys.isfreebsd([os])
```

Prädikat zum Testen, ob das Betriebssystem ein Derivat von FreeBSD ist. Siehe Dokumentation in [Handling Operating System Variation](@ref).

!!! Hinweis     Nicht zu verwechseln mit `Sys.isbsd()`, das `true` auf FreeBSD, aber auch auf anderen BSD-basierten Systemen ist. `Sys.isfreebsd()` bezieht sich nur auf FreeBSD.

!!! Kompatibilität "Julia 1.1"     Diese Funktion erfordert mindestens Julia 1.1.
