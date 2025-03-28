```
empty(a::AbstractDict, [index_type=keytype(a)], [value_type=valtype(a)])
```

Crea un contenedor `AbstractDict` vacío que puede aceptar índices del tipo `index_type` y valores del tipo `value_type`. Los segundo y tercero argumentos son opcionales y por defecto son el `keytype` y `valtype` de la entrada, respectivamente. (Si solo se especifica uno de los dos tipos, se asume que es el `value_type`, y el `index_type` por defecto será `keytype(a)`).

Los subtipos personalizados de `AbstractDict` pueden elegir qué tipo de diccionario específico es el más adecuado para devolver para los tipos de índice y valor dados, especializándose en la firma de tres argumentos. El valor por defecto es devolver un `Dict` vacío.
