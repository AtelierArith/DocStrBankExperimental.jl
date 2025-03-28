```
format(dt::TimeType, format::AbstractString; locale="español") -> AbstractString
```

Construya una cadena utilizando un objeto `TimeType` y aplicando el `formato` proporcionado. Los siguientes códigos de caracteres se pueden usar para construir la cadena `formato`:

| Código | Ejemplos | Comentario                                                |
|:------ |:-------- |:--------------------------------------------------------- |
| `y`    | 6        | Año numérico con un ancho fijo                            |
| `Y`    | 1996     | Año numérico con un ancho mínimo                          |
| `m`    | 1, 12    | Mes numérico con un ancho mínimo                          |
| `u`    | Ene      | Nombre del mes abreviado a 3 caracteres según el `locale` |
| `U`    | Enero    | Nombre completo del mes según la palabra clave `locale`   |
| `d`    | 1, 31    | Día del mes con un ancho mínimo                           |
| `H`    | 0, 23    | Hora (reloj de 24 horas) con un ancho mínimo              |
| `M`    | 0, 59    | Minuto con un ancho mínimo                                |
| `S`    | 0, 59    | Segundo con un ancho mínimo                               |
| `s`    | 000, 500 | Milisegundo con un ancho mínimo de 3                      |
| `e`    | Lun, Mar | Días de la semana abreviados                              |
| `E`    | Lunes    | Nombre completo del día de la semana                      |

El número de caracteres de código secuenciales indica el ancho del código. Un formato de `yyyy-mm` especifica que el código `y` debe tener un ancho de cuatro, mientras que `m` un ancho de dos. Los códigos que producen dígitos numéricos tienen un modo asociado: ancho fijo o ancho mínimo. El modo de ancho fijo rellena a la izquierda el valor con ceros cuando es más corto que el ancho especificado y trunca el valor cuando es más largo. El modo de ancho mínimo funciona igual que el ancho fijo, excepto que no trunca los valores más largos que el ancho.

Al crear un `formato`, puede usar cualquier carácter que no sea un código como separador. Por ejemplo, para generar la cadena "1996-01-15T00:00:00" podría usar `formato`: "yyyy-mm-ddTHH:MM:SS". Tenga en cuenta que si necesita usar un carácter de código como literal, puede usar el carácter de escape barra invertida. La cadena "1996y01m" se puede producir con el formato "yyyy\ymm\m".
