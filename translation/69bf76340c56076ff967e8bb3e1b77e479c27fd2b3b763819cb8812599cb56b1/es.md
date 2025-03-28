```
isunaryoperator(s::Symbol)
```

Devuelve `true` si el símbolo puede ser utilizado como un operador unario (prefijo), `false` en caso contrario.

# Ejemplos

```jldoctest
julia> Meta.isunaryoperator(:-), Meta.isunaryoperator(:√), Meta.isunaryoperator(:f)
(true, true, false)
```
