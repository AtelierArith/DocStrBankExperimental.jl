```
pick(m::AbstractMenu, cursor::Int)
```

Define lo que sucede cuando un usuario presiona la tecla Enter mientras el menú está abierto. Si se devuelve `true`, `request()` saldrá. `cursor` indexa la posición de la selección.
