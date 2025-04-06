```
replaceproperty!(x, f::Symbol, expected, desired, success_order::Symbol=:not_atomic, fail_order::Symbol=success_order)
```

Realiza una operación de comparación e intercambio en `x.f` de `expected` a `desired`, según egal. La sintaxis `@atomicreplace x.f expected => desired` se puede usar en lugar de la forma de llamada a la función.

Véase también [`replacefield!`](@ref Core.replacefield!) [`setproperty!`](@ref Base.setproperty!), [`setpropertyonce!`](@ref Base.setpropertyonce!).
