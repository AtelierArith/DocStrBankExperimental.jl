```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

Establece el tipo declarado de la vinculación `name` en el módulo `module` a `type`. Genera un error si la vinculación ya tiene un tipo que no es equivalente a `type`. Si el argumento `type` está ausente, establece el tipo de vinculación en `Any` si no está configurado, pero no genera un error.

!!! compat "Julia 1.9"
    Esta función requiere Julia 1.9 o posterior.

