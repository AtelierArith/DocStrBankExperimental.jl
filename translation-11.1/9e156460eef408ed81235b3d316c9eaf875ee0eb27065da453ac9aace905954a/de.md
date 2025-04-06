```
@lock l expr
```

Makroversion von `lock(f, l::AbstractLock)`, aber mit `expr` anstelle der `f`-Funktion. Erweitert sich zu:

```julia
lock(l)
try
    expr
finally
    unlock(l)
end
```

Dies ist ähnlich wie die Verwendung von [`lock`](@ref) mit einem `do`-Block, vermeidet jedoch die Erstellung einer Closure und kann somit die Leistung verbessern.

!!! kompatibel
    `@lock` wurde in Julia 1.3 hinzugefügt und in Julia 1.10 exportiert.

