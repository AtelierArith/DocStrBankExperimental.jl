```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

Effectuer atomiquement les opérations pour obtenir et définir un champ après avoir appliqué la fonction `op`.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

Si pris en charge par le matériel (par exemple, incrément atomique), cela peut être optimisé vers l'instruction matérielle appropriée, sinon cela utilisera une boucle.

!!! compat "Julia 1.7"
    Cette fonction nécessite Julia 1.7 ou une version ultérieure.

