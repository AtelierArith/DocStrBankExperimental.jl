```
GC.enable(on::Bool)
```

Controla si la recolección de basura está habilitada utilizando un argumento booleano (`true` para habilitado, `false` para deshabilitado). Devuelve el estado anterior de la recolección de basura.

!!! warning
    Deshabilitar la recolección de basura debe usarse solo con precaución, ya que puede hacer que el uso de memoria crezca sin límites.

