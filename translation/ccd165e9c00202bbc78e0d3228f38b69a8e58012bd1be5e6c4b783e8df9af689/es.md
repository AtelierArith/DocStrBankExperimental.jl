```
<(x, y)
```

Operador de comparación menor que. Recurre a [`isless`](@ref). Debido al comportamiento de los valores NaN de punto flotante, este operador implementa un orden parcial.

# Implementación

Los nuevos tipos con un orden parcial canónico deben implementar esta función para dos argumentos del nuevo tipo. Los tipos con un orden total canónico deben implementar [`isless`](@ref) en su lugar.

Véase también [`isunordered`](@ref).

# Ejemplos

```jldoctest
julia> 'a' < 'b'
true

julia> "abc" < "abd"
true

julia> 5 < 3
false
```
