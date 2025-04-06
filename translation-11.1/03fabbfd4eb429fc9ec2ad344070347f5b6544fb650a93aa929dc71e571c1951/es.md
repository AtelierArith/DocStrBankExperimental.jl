```
get_zero_subnormals() -> Bool
```

Devuelve `false` si las operaciones en valores de punto flotante subnormales ("denormales") obedecen las reglas de la aritmética IEEE, y `true` si podrían convertirse en ceros.

!!! warning
    Esta función solo afecta al hilo actual.

