```
chown(path::AbstractString, owner::Integer, group::Integer=-1)
```

Cambia el propietario y/o grupo de `path` a `owner` y/o `group`. Si el valor ingresado para `owner` o `group` es `-1`, el ID correspondiente no cambiará. Actualmente, solo se admiten `owner`s y `group`s enteros. Devuelve `path`.
