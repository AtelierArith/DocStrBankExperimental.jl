```
Sys.isopenbsd([os])
```

Prädikat zum Testen, ob das Betriebssystem ein Derivat von OpenBSD ist. Siehe Dokumentation in [Handling Operating System Variation](@ref).

!!! note
    Nicht zu verwechseln mit `Sys.isbsd()`, das `true` auf OpenBSD, aber auch auf anderen BSD-basierten Systemen ist. `Sys.isopenbsd()` bezieht sich nur auf OpenBSD.


!!! compat "Julia 1.1"
    Diese Funktion erfordert mindestens Julia 1.1.

