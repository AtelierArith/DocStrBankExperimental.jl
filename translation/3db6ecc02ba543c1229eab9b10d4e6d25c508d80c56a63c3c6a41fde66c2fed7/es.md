```
DateTime(f::Function, y[, m, d, h, mi, s]; step=Day(1), limit=10000) -> DateTime
```

Crea un `DateTime` a través de la API de ajustadores. El punto de partida se construirá a partir de los argumentos proporcionados `y, m, d...`, y se ajustará hasta que `f::Function` devuelva `true`. El tamaño del paso en el ajuste se puede proporcionar manualmente a través de la palabra clave `step`. `limit` proporciona un límite al número máximo de iteraciones que la API de ajuste perseguirá antes de lanzar un error (en el caso de que `f::Function` nunca se satisfaga).

# Ejemplos

```jldoctest
julia> DateTime(dt -> second(dt) == 40, 2010, 10, 20, 10; step = Second(1))
2010-10-20T10:00:40

julia> DateTime(dt -> hour(dt) == 20, 2010, 10, 20, 10; step = Hour(1), limit = 5)
ERROR: ArgumentError: Límite de ajuste alcanzado: 5 iteraciones
Stacktrace:
[...]
```
