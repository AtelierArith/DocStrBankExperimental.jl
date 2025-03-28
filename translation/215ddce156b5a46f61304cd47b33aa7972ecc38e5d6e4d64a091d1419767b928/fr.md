```
Time(f::Function, h, mi=0; step::Period=Second(1), limit::Int=10000)
Time(f::Function, h, mi, s; step::Period=Millisecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms; step::Period=Microsecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms, us; step::Period=Nanosecond(1), limit::Int=10000)
```

Créez un `Time` via l'API d'ajustement. Le point de départ sera construit à partir des arguments fournis `h, mi, s, ms, us`, et sera ajusté jusqu'à ce que `f::Function` retourne `true`. La taille du pas dans l'ajustement peut être fournie manuellement via le mot-clé `step`. `limit` fournit une limite au nombre maximum d'itérations que l'API d'ajustement poursuivra avant de lancer une erreur (dans le cas où `f::Function` n'est jamais satisfait). Notez que le pas par défaut s'ajustera pour permettre une plus grande précision pour les arguments donnés ; c'est-à-dire que si des arguments d'heure, de minute et de seconde sont fournis, le pas par défaut sera `Millisecond(1)` au lieu de `Second(1)`.

# Exemples

```jldoctest
julia> Time(t -> minute(t) == 30, 20)
20:30:00

julia> Time(t -> minute(t) == 0, 20)
20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5)
ERROR: ArgumentError: Limite d'ajustement atteinte : 5 itérations
Stacktrace:
[...]
```
