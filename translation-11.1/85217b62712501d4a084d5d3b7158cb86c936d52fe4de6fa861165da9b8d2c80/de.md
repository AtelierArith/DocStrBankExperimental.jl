```
lazy"str"
```

Erstellen Sie einen [`LazyString`](@ref) mit der regulären String-Interpolation-Syntax. Beachten Sie, dass Interpolationen *zum Zeitpunkt der Konstruktion von LazyString* *ausgewertet* werden, aber das *Drucken* bis zum ersten Zugriff auf den String *verzögert* wird.

Siehe die [`LazyString`](@ref) Dokumentation für die Sicherheitsmerkmale für nebenläufige Programme.

# Beispiele

```
julia> n = 5; str = lazy"n ist $n"
"n ist 5"

julia> typeof(str)
LazyString
```

!!! compat "Julia 1.8"
    `lazy"str"` erfordert Julia 1.8 oder höher.

