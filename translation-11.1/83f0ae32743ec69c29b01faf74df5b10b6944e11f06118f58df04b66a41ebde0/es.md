```
isbinaryoperator(s::Symbol)
```

Devuelve `true` si el símbolo puede ser utilizado como un operador binario (infixo), `false` en caso contrario.

# Ejemplos

```jldoctest
julia> Meta.isbinaryoperator(:-), Meta.isbinaryoperator(:√), Meta.isbinaryoperator(:f)
(true, false, false)
```
