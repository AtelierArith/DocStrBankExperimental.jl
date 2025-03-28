```
isoperator(s::Symbol)
```

Devuelve `true` si el símbolo puede ser utilizado como un operador, `false` en caso contrario.

# Ejemplos

```jldoctest
julia> Meta.isoperator(:+), Meta.isoperator(:f)
(true, false)
```
