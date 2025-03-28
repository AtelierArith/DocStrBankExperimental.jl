```
sizehint!(s, n; first::Bool=false, shrink::Bool=true) -> s
```

Sugiere que la colección `s` reserve capacidad para al menos `n` elementos. Es decir, si esperas que vas a tener que agregar muchos valores a `s`, puedes evitar el costo de la realocación incremental haciéndolo una vez al principio; esto puede mejorar el rendimiento.

Si `first` es `true`, entonces se reserva espacio adicional antes del inicio de la colección. De esta manera, las llamadas subsiguientes a `pushfirst!` (en lugar de `push!`) pueden volverse más rápidas. Suministrar esta palabra clave puede resultar en un error si la colección no está ordenada o si `pushfirst!` no es compatible con esta colección.

Si `shrink=true` (el valor predeterminado), la capacidad de la colección puede reducirse si su capacidad actual es mayor que `n`.

Ver también [`resize!`](@ref).

# Notas sobre el modelo de rendimiento

Para tipos que soportan `sizehint!`,

1. Los métodos `push!` y `append!` generalmente pueden (pero no están obligados a) preasignar almacenamiento adicional. Para tipos implementados en `Base`, típicamente lo hacen, utilizando una heurística optimizada para un caso de uso general.
2. `sizehint!` puede controlar esta preasignación. Nuevamente, típicamente lo hace para tipos en `Base`.
3. `empty!` es casi sin costo (y O(1)) para tipos que soportan este tipo de preasignación.

!!! compat "Julia 1.11"
    Los argumentos `shrink` y `first` se añadieron en Julia 1.11.

