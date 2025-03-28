```
setrounding(T, mode)
```

Establece el modo de redondeo del tipo de punto flotante `T`, controlando el redondeo de las funciones aritméticas básicas ([`+`](@ref), [`-`](@ref), [`*`](@ref), [`/`](@ref) y [`sqrt`](@ref)) y la conversión de tipos. Otras funciones numéricas pueden dar valores incorrectos o inválidos al usar modos de redondeo diferentes del predeterminado [`RoundNearest`](@ref).

Tenga en cuenta que esto actualmente solo es compatible con `T == BigFloat`.

!!! warning
    Esta función no es segura para hilos. Afectará el código que se ejecute en todos los hilos, pero su comportamiento es indefinido si se llama de manera concurrente con cálculos que utilizan la configuración.

