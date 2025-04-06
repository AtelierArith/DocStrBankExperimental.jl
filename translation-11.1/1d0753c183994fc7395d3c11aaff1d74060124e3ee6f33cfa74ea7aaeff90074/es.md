```
Date(f::Function, y[, m, d]; step=Day(1), limit=10000) -> Date
```

Crea un `Date` a través de la API de ajustadores. El punto de partida se construirá a partir de los argumentos proporcionados `y, m, d`, y se ajustará hasta que `f::Function` devuelva `true`. El tamaño del paso en el ajuste se puede proporcionar manualmente a través de la palabra clave `step`. `limit` proporciona un límite al número máximo de iteraciones que la API de ajuste perseguirá antes de lanzar un error (dado que `f::Function` nunca se satisface).

# Ejemplos

```jldoctest
julia> Date(date -> week(date) == 20, 2010, 01, 01)
2010-05-17

julia> Date(date -> year(date) == 2010, 2000, 01, 01)
2010-01-01

julia> Date(date -> month(date) == 10, 2000, 01, 01; limit = 5)
ERROR: ArgumentError: Límite de ajuste alcanzado: 5 iteraciones
Stacktrace:
[...]
```
