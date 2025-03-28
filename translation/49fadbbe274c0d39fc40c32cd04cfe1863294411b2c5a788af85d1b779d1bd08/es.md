```
Base.Pairs(values, keys) <: AbstractDict{eltype(keys), eltype(values)}
```

Transforma un contenedor indexable en una vista de Diccionario de los mismos datos. Modificar el espacio de claves de los datos subyacentes puede invalidar este objeto.
