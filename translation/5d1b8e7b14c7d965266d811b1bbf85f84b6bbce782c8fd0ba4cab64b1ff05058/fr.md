```
maxintfloat(T=Float64)
```

Le plus grand nombre à virgule flottante de valeur entière consécutive qui est exactement représenté dans le type de virgule flottante donné `T` (qui par défaut est `Float64`).

C'est-à-dire que `maxintfloat` renvoie le plus petit nombre à virgule flottante de valeur entière positive `n` tel que `n+1` n'est *pas* exactement représentable dans le type `T`.

Lorsqu'une valeur de type `Integer` est nécessaire, utilisez `Integer(maxintfloat(T))`.
