```
setpropertyonce!(x, f::Symbol, value, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Realiza una operación de comparación e intercambio en `x.f` para establecerlo en `value` si anteriormente no estaba establecido. La sintaxis `@atomiconce x.f = value` se puede usar en lugar de la forma de llamada a la función.

Véase también [`setfieldonce!`](@ref Core.replacefield!), [`setproperty!`](@ref Base.setproperty!), [`replaceproperty!`](@ref Base.replaceproperty!).

!!! compat "Julia 1.11"
    Esta función requiere Julia 1.11 o posterior.

