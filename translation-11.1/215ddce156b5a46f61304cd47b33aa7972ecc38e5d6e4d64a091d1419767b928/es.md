```
Time(f::Function, h, mi=0; step::Period=Second(1), limit::Int=10000)
Time(f::Function, h, mi, s; step::Period=Millisecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms; step::Period=Microsecond(1), limit::Int=10000)
Time(f::Function, h, mi, s, ms, us; step::Period=Nanosecond(1), limit::Int=10000)
```

Crea un `Time` a través de la API de ajustador. El punto de partida se construirá a partir de los argumentos proporcionados `h, mi, s, ms, us`, y se ajustará hasta que `f::Function` devuelva `true`. El tamaño del paso en el ajuste se puede proporcionar manualmente a través de la palabra clave `step`. `limit` proporciona un límite al número máximo de iteraciones que la API de ajuste perseguirá antes de lanzar un error (en el caso de que `f::Function` nunca se satisfaga). Tenga en cuenta que el paso predeterminado se ajustará para permitir una mayor precisión para los argumentos dados; es decir, si se proporcionan argumentos de hora, minuto y segundo, el paso predeterminado será `Millisecond(1)` en lugar de `Second(1)`.

# Ejemplos

```jldoctest
julia> Time(t -> minute(t) == 30, 20)
20:30:00

julia> Time(t -> minute(t) == 0, 20)
20:00:00

julia> Time(t -> hour(t) == 10, 3; limit = 5)
ERROR: ArgumentError: Límite de ajuste alcanzado: 5 iteraciones
Stacktrace:
[...]
```
