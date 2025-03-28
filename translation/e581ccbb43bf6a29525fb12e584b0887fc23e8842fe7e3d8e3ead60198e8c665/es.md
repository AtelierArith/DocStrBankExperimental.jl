```
ifelse(condition::Bool, x, y)
```

Devuelve `x` si `condition` es `true`, de lo contrario devuelve `y`. Esto difiere de `?` o `if` en que es una función ordinaria, por lo que todos los argumentos se evalúan primero. En algunos casos, usar `ifelse` en lugar de una declaración `if` puede eliminar la rama en el código generado y proporcionar un mayor rendimiento en bucles ajustados.

# Ejemplos

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
