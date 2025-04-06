```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Effectuer atomiquement les opérations pour obtenir et conditionnellement définir un champ à une valeur donnée.

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

Si pris en charge par le matériel, cela peut être optimisé pour l'instruction matérielle appropriée, sinon cela utilisera une boucle.

!!! compat "Julia 1.7"
    Cette fonction nécessite Julia 1.7 ou une version ultérieure.

