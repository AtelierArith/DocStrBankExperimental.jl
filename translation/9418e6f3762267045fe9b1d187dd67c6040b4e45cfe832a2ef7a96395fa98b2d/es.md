```
replacefield!(value, name::Symbol, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
replacefield!(value, i::Int, expected, desired,
              [success_order::Symbol, [fail_order::Symbol=success_order]) -> (; old, success::Bool)
```

Realiza atómicamente las operaciones para obtener y condicionalmente establecer un campo a un valor dado.

```
y = getfield(value, name, fail_order)
ok = y === expected
if ok
    setfield!(value, name, desired, success_order)
end
return (; old = y, success = ok)
```

Si es compatible con el hardware, esto puede optimizarse a la instrucción de hardware apropiada; de lo contrario, utilizará un bucle.

!!! compat "Julia 1.7"
    Esta función requiere Julia 1.7 o posterior.

