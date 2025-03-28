```
factorial(n::Integer)
```

Factorial de `n`. Si `n` es un [`Integer`](@ref), el factorial se calcula como un entero (promovido a al menos 64 bits). Ten en cuenta que esto puede desbordarse si `n` no es pequeño, pero puedes usar `factorial(big(n))` para calcular el resultado exactamente en precisión arbitraria.

Ver también [`binomial`](@ref).

# Ejemplos

```jldoctest
julia> factorial(6)
720

julia> factorial(21)
ERROR: OverflowError: 21 es demasiado grande para buscar en la tabla; considera usar `factorial(big(21))` en su lugar
Stacktrace:
[...]

julia> factorial(big(21))
51090942171709440000
```

# Enlaces externos

  * [Factorial](https://en.wikipedia.org/wiki/Factorial) en Wikipedia.

```
