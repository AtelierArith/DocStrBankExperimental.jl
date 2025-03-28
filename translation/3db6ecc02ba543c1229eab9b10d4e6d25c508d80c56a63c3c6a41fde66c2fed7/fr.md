```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

Créez un `DateTime` via l'API d'ajustement. Le point de départ sera construit à partir des arguments fournis `y, m, d...`, et sera ajusté jusqu'à ce que `f::Function` retourne `true`. La taille du pas dans l'ajustement peut être fournie manuellement via le mot-clé `step`. `limit` fournit une limite au nombre maximum d'itérations que l'API d'ajustement poursuivra avant de lancer une erreur (dans le cas où `f::Function` n'est jamais satisfait).

# Exemples

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
ERROR: ArgumentError: Limite d'ajustement atteinte : 5 itérations
Stacktrace:
[...]
```
