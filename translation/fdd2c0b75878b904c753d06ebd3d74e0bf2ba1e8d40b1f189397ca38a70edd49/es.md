```
request(m::AbstractMenu; cursor=1)
```

Muestra el menú e ingresa al modo interactivo. `cursor` indica el número del ítem utilizado para la posición inicial del cursor. `cursor` puede ser un `Int` o un `RefValue{Int}`. Este último es útil para la observación y el control de la posición del cursor desde el exterior.

Devuelve `selected(m)`.

!!! compat "Julia 1.6"
    El argumento `cursor` requiere Julia 1.6 o posterior.

