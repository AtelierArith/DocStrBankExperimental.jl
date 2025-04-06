```
quote
```

`quote` crea múltiples objetos de expresión en un bloque sin usar el constructor explícito [`Expr`](@ref). Por ejemplo:

```julia
ex = quote
    x = 1
    y = 2
    x + y
end
```

A diferencia de otros medios de citar, `:( ... )`, esta forma introduce elementos `QuoteNode` en el árbol de expresiones, que deben ser considerados al manipular directamente el árbol. Para otros propósitos, `:( ... )` y los bloques `quote .. end` se tratan de manera idéntica.
