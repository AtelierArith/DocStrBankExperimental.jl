```
set_zero_subnormals(yes::Bool) -> Bool
```

Si `yes` es `false`, las operaciones de punto flotante subsiguientes siguen las reglas de la aritmética IEEE sobre valores subnormales ("denormales"). De lo contrario, se permite (pero no se requiere) que las operaciones de punto flotante conviertan entradas o salidas subnormales a cero. Devuelve `true` a menos que `yes==true` pero el hardware no soporte la anulación de números subnormales.

`set_zero_subnormals(true)` puede acelerar algunos cálculos en cierto hardware. Sin embargo, puede romper identidades como `(x-y==0) == (x==y)`.

!!! advertencia
    Esta función solo afecta el hilo actual.

