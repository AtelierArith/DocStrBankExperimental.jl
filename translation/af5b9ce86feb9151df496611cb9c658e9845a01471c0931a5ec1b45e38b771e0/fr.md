```
clear!(syms, pids=workers(); mod=Main)
```

Efface les liaisons globales dans les modules en les initialisant à `nothing`. `syms` doit être de type [`Symbol`](@ref) ou une collection de `Symbol`s. `pids` et `mod` identifient les processus et le module dans lequel les variables globales doivent être réinitialisées. Seuls les noms trouvés définis sous `mod` sont effacés.

Une exception est levée si une constante globale est demandée à être effacée.
