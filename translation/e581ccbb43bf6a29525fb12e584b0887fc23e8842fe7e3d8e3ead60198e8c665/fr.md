```
ifelse(condition::Bool, x, y)
```

Retourne `x` si `condition` est `true`, sinon retourne `y`. Cela diffère de `?` ou `if` en ce sens que c'est une fonction ordinaire, donc tous les arguments sont évalués en premier. Dans certains cas, utiliser `ifelse` au lieu d'une instruction `if` peut éliminer la branche dans le code généré et fournir de meilleures performances dans des boucles serrées.

# Exemples

```jldoctest
julia> ifelse(1 > 2, 1, 2)
2
```
