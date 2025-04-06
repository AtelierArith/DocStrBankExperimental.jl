```
DateFormat(format::AbstractString, locale="español") -> DateFormat
```

Construye un objeto de formato de fecha que se puede usar para analizar cadenas de fecha o formatear un objeto de fecha como una cadena. Los siguientes códigos de caracteres se pueden usar para construir la cadena `format`:

| Código     | Coincide | Comentario                                                              |
|:---------- |:-------- |:----------------------------------------------------------------------- |
| `Y`        | 1996, 96 | Devuelve el año de 1996, 0096                                           |
| `y`        | 1996, 96 | Igual que `Y` en `parse` pero descarta dígitos excesivos en `format`    |
| `m`        | 1, 01    | Coincide con meses de 1 o 2 dígitos                                     |
| `u`        | Ene      | Coincide con meses abreviados según la palabra clave `locale`           |
| `U`        | Enero    | Coincide con nombres completos de meses según la palabra clave `locale` |
| `d`        | 1, 01    | Coincide con días de 1 o 2 dígitos                                      |
| `H`        | 00       | Coincide con horas (reloj de 24 horas)                                  |
| `I`        | 00       | Para mostrar horas con reloj de 12 horas                                |
| `M`        | 00       | Coincide con minutos                                                    |
| `S`        | 00       | Coincide con segundos                                                   |
| `s`        | .500     | Coincide con milisegundos                                               |
| `e`        | Lun, Mar | Coincide con días de la semana abreviados                               |
| `E`        | Lunes    | Coincide con nombres completos de días de la semana                     |
| `p`        | AM       | Coincide con AM/PM (sin distinción de mayúsculas y minúsculas)          |
| `yyyymmdd` | 19960101 | Coincide con año, mes y día de ancho fijo                               |

Los caracteres no listados arriba se tratan normalmente como delimitadores entre las partes de fecha y hora. Por ejemplo, una cadena `dt` de "1996-01-15T00:00:00.0" tendría una cadena `format` como "y-m-dTH:M:S.s". Si necesitas usar un carácter de código como delimitador, puedes escaparlo usando una barra invertida. La fecha "1995y01m" tendría el formato "y\ym\m".

Ten en cuenta que 12:00AM corresponde a 00:00 (medianoche), y 12:00PM corresponde a 12:00 (mediodía). Al analizar una hora con un especificador `p`, cualquier hora (ya sea `H` o `I`) se interpreta como un reloj de 12 horas, por lo que el código `I` es principalmente útil para la salida.

Crear un objeto DateFormat es costoso. Siempre que sea posible, créalo una vez y úsalo muchas veces o prueba el macro de cadena [`dateformat""`](@ref @dateformat_str). Usar este macro crea el objeto DateFormat una vez en el momento de la expansión del macro y lo reutiliza más tarde. También hay varios [formateadores predefinidos](@ref Common-Date-Formatters), que se enumeran más adelante.

Consulta [`DateTime`](@ref) y [`format`](@ref) para saber cómo usar un objeto DateFormat para analizar y escribir cadenas de fecha respectivamente.
