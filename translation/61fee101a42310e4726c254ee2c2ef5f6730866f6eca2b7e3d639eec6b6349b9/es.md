```
swapfield!(value, name::Symbol, x, [order::Symbol])
swapfield!(value, i::Int, x, [order::Symbol])
```

Realiza atómicamente las operaciones para obtener y establecer simultáneamente un campo:

```
y = getfield(value, name)
setfield!(value, name, x)
return y
```

!!! compat "Julia 1.7"
    Esta función requiere Julia 1.7 o posterior.

