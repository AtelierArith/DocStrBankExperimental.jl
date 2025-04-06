```
function
```

Las funciones se definen con la palabra clave `function`:

```julia
function add(a, b)
    return a + b
end
```

O la notación en forma corta:

```julia
add(a, b) = a + b
```

El uso de la palabra clave [`return`](@ref) es exactamente el mismo que en otros lenguajes, pero a menudo es opcional. Una función sin una declaración `return` explícita devolverá la última expresión en el cuerpo de la función.
