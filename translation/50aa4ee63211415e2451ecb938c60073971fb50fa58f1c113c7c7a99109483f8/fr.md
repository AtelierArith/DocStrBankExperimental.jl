```
setfieldonce!(value, name::Union{Int,Symbol}, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> success::Bool
```

Effectuer atomiquement les opérations pour définir un champ à une valeur donnée, uniquement s'il n'a pas été précédemment défini.

```
ok = !isdefined(value, name, fail_order)
if ok
    setfield!(value, name, desired, success_order)
end
return ok
```

!!! compat "Julia 1.11"
    Cette fonction nécessite Julia 1.11 ou une version ultérieure.

