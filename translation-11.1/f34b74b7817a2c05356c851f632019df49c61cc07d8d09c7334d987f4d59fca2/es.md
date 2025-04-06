```
modifyfield!(value, name::Symbol, op, x, [order::Symbol]) -> Pair
modifyfield!(value, i::Int, op, x, [order::Symbol]) -> Pair
```

Realiza de manera atómica las operaciones para obtener y establecer un campo después de aplicar la función `op`.

```
y = getfield(value, name)
z = op(y, x)
setfield!(value, name, z)
return y => z
```

Si es compatible con el hardware (por ejemplo, incremento atómico), esto puede optimizarse a la instrucción de hardware apropiada; de lo contrario, utilizará un bucle.

!!! compat "Julia 1.7"
    Esta función requiere Julia 1.7 o posterior.

