```
Serialization.writeheader(s::AbstractSerializer)
```

Escribe un encabezado identificador para el serializador especificado. El encabezado consiste en 8 bytes de la siguiente manera:

| Desplazamiento | Descripción                                    |
|:-------------- |:---------------------------------------------- |
| 0              | byte de etiqueta (0x37)                        |
| 1-2            | bytes de firma "JL"                            |
| 3              | versión del protocolo                          |
| 4              | bits 0-1: orden de bytes: 0 = poco, 1 = grande |
| 4              | bits 2-3: plataforma: 0 = 32 bits, 1 = 64 bits |
| 5-7            | reservado                                      |
