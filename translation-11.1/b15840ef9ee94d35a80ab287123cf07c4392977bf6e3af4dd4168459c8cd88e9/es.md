```
modf(x)
```

Devuelve una tupla `(fpart, ipart)` de las partes fraccionaria e integral de un número. Ambas partes tienen el mismo signo que el argumento.

# Ejemplos

```jldoctest
julia> modf(3.5)
(0.5, 3.0)

julia> modf(-3.5)
(-0.5, -3.0)
```
