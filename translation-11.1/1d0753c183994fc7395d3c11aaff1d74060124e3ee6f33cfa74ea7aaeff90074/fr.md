```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

Créez un `Date` via l'API d'ajustement. Le point de départ sera construit à partir des arguments fournis `y, m, d`, et sera ajusté jusqu'à ce que `f::Function` retourne `true`. La taille du pas dans l'ajustement peut être fournie manuellement via le mot-clé `step`. `limit` fournit une limite au nombre maximum d'itérations que l'API d'ajustement poursuivra avant de lancer une erreur (étant donné que `f::Function` n'est jamais satisfait).

# Exemples

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
ERROR: ArgumentError: Limite d'ajustement atteinte : 5 itérations
Stacktrace:
[...]
```
