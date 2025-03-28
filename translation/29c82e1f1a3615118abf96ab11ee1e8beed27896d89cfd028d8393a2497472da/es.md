```
detect_unbound_args(mod1, mod2...; recursive=false, allowed_undefineds=nothing)
```

Devuelve un vector de `Method`s que pueden tener parámetros de tipo no vinculados. Usa `recursive=true` para probar en todos los submódulos.

Por defecto, cualquier símbolo no definido desencadena una advertencia. Esta advertencia se puede suprimir proporcionando una colección de `GlobalRef`s para las cuales se puede omitir la advertencia. Por ejemplo, configurando

```
allowed_undefineds = Set([GlobalRef(Base, :active_repl),
                          GlobalRef(Base, :active_repl_backend)])
```

suprimiría las advertencias sobre `Base.active_repl` y `Base.active_repl_backend`.

!!! compat "Julia 1.8"
    `allowed_undefineds` requiere al menos Julia 1.8.

