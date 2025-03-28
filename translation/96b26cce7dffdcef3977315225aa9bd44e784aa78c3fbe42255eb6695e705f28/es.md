```
if/elseif/else
```

`if`/`elseif`/`else` realiza una evaluación condicional, lo que permite que partes del código se evalúen o no se evalúen dependiendo del valor de una expresión booleana. Aquí está la anatomía de la sintaxis condicional `if`/`elseif`/`else`:

```julia
if x < y
    println("x es menor que y")
elseif x > y
    println("x es mayor que y")
else
    println("x es igual a y")
end
```

Si la expresión de condición `x < y` es verdadera, entonces el bloque correspondiente se evalúa; de lo contrario, se evalúa la expresión de condición `x > y`, y si es verdadera, se evalúa el bloque correspondiente; si ninguna de las expresiones es verdadera, se evalúa el bloque `else`. Los bloques `elseif` y `else` son opcionales, y se pueden usar tantos bloques `elseif` como se desee.

A diferencia de algunos otros lenguajes, las condiciones deben ser de tipo `Bool`. No es suficiente que las condiciones sean convertibles a `Bool`.

```jldoctest
julia> if 1 end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
