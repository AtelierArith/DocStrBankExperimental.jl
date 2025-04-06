```
return
```

`return x` hace que la función que lo contiene salga anticipadamente, pasando el valor dado `x` de vuelta a su llamador. `return` por sí solo sin un valor es equivalente a `return nothing` (ver [`nothing`](@ref)).

```julia
function compare(a, b)
    a == b && return "equal to"
    a < b ? "less than" : "greater than"
end
```

En general, puedes colocar una declaración `return` en cualquier lugar dentro del cuerpo de una función, incluyendo dentro de bucles o condicionales profundamente anidados, pero ten cuidado con los bloques `do`. Por ejemplo:

```julia
function test1(xs)
    for x in xs
        iseven(x) && return 2x
    end
end

function test2(xs)
    map(xs) do x
        iseven(x) && return 2x
        x
    end
end
```

En el primer ejemplo, el return sale de `test1` tan pronto como encuentra un número par, por lo que `test1([5,6,7])` devuelve `12`.

Podrías esperar que el segundo ejemplo se comportara de la misma manera, pero de hecho el `return` allí solo sale de la *función interna* (dentro del bloque `do`) y devuelve un valor a `map`. `test2([5,6,7])` entonces devuelve `[5,12,7]`.

Cuando se usa en una expresión de nivel superior (es decir, fuera de cualquier función), `return` hace que toda la expresión de nivel superior actual termine anticipadamente.
